Mozilla CA Certificate Inclusion Policy
=======================================

### (DRAFT Version 2.3)

This section of the [Mozilla CA Certificate Policy][policy] describes the
obligations of Certification Authorities applying for inclusion of their root
certificates in Mozilla Products. This includes considerations that are taken
into account such as the CA’s publicly available documentation about their
policies, and audits of the CA’s operations in support of the documented
policies.

This is the official Mozilla policy for Certification Authorities applying for
inclusion of their CA Certificates to be distributed in Mozilla products:


1. We will determine which CA certificates are included in software
   products distributed by Mozilla, based on the benefits and risks of such
   inclusion to typical users of those products.

2. We will make such decisions through a public process, based on objective and
   verifiable criteria as described below.

3. We will not charge any fees to have a CA’s certificate(s) distributed with
   our software products.

4. We reserve the right to not include a particular CA certificate in
   our software products. This includes (but is not limited to) cases
   where we believe that including a CA certificate (or setting its "trust
   bits" in a particular way) would cause undue risks to users’ security,
   for example, with CAs that

   * knowingly issue certificates without the knowledge of the entities whose
     information is referenced in the certificates; *or*

   * knowingly issue certificates that appear to be intended for fraudulent
     use.

   This also includes (but again is not limited to) cases where we
   believe that including a CA certificate (or setting its "trust bits" in a
    particular way) might cause technical problems with the operation of
   our software, for example, with CAs that issue certificates that have

   * ASN.1 DER encoding errors;

   * invalid public keys (e.g., RSA certificates with public exponent equal to
     1);

   * duplicate issuer names and serial numbers;

   * incorrect extensions (e.g., SSL certificates that exclude SSL usage, or
     authority key IDs that include both the key ID and the issuer’s issuer
     name and serial number); *or*

   * cRLDistributionPoints or OCSP authorityInfoAccess extensions for which no
     operational CRL or OCSP service exists.

5. We will consider adding certificates for additional CAs to the
   default certificate set upon request only by an authorized
   representative of the subject CA.

6. We require that all CAs whose certificates are distributed with our software
   products:

   * provide some service relevant to typical users of our software products;

   * publicly disclose information about their policies and
     business practices (e.g., in a Certificate Policy and Certification
     Practice Statement);

   * enforce multi-factor authentication for all accounts capable
     of directly causing certificate issuance or implement technical controls
     operated by the CA to restrict certificate issuance through the account
     to a limited set of pre-approved domains or email addresses;

   * maintain a certificate hierarchy such that the included certificate does
     not directly issue end-entity certificates to customers (e.g., the
     included certificate signs intermediate issuing certificates), as
     described in section 6.1.7 of the [CA/Browser Forum’s Baseline
     Requirements][CABF];

   * prior to issuing certificates, verify certificate signing
     requests in a manner that we deem acceptable for the stated purpose(s)
     of the certificates;

   * verify that all of the information that is included in SSL
     certificates remains current and correct at time intervals of
     thirty-nine months or less;

   * otherwise operate in accordance with published criteria that we deem
     acceptable; *and*

   * provide public attestation of their conformance to the stated
     verification requirements and other operational criteria by a competent
     independent party or parties with access to details of the CA’s internal
     operations.

7. We consider verification of certificate signing requests to be acceptable if
   it meets or exceeds the following requirements:

   * all information that is supplied by the certificate subscriber
     must be verified by using an independent source of information or an
     alternative communication channel before it is included in the
     certificate;

   * for a certificate to be used for digitally signing or
     encrypting email messages, the CA takes reasonable measures to verify that
     the entity submitting the request controls the email account associated
     with the email address referenced in the certificate *or* has been
     authorized by the email account holder to act on the account holder’s
     behalf;

   * for a certificate to be used for SSL-enabled servers, the CA takes
     reasonable measures to verify that the entity submitting the certificate
     signing request has registered the domain(s) referenced in the certificate
     *or* has been authorized by the domain registrant to act on the
     registrant’s behalf;

   * for certificates to be used for and marked as Extended Validation, the CA
     complies with [Guidelines for the Issuance and Management of Extended
     Validation Certificates][CABF] version 1.4 or later.

    We reserve the right to use other requirements in the future.

8. All certificates that are capable of being used to issue new certificates,
   and which directly or transitively chain to a certificate included in
   Mozilla’s CA Certificate Program, MUST be operated in accordance with
   [Mozilla’s CA Certificate Policy][policy] and MUST either be **technically
   constrained** or be **publicly disclosed and audited**.

   * A certificate is deemed as capable of being used to issue new certificates
     if it contains an [X.509v3 basicConstraints extension][basicConstraints],
     with the cA boolean set to true. The term "subordinate CA" below refers to
     any organization or legal entity that is in possession or control of a
     certificate that is capable of being used to issue new certificates.

   * These requirements include all cross-certified certificates which chain to
     a certificate that is included in Mozilla’s CA Certificate Program.

9. We encourage CAs to technically constrain all subordinate CA certificates.
   For a certificate to be considered **technically constrained,** the
   certificate MUST include an [Extended Key Usage (EKU)][extKeyUsage]
   extension specifying all extended key usages that the subordinate CA is
   authorized to issue certificates for. The anyExtendedKeyUsage KeyPurposeId
   MUST NOT appear within this extension.'

   * If the certificate includes the id-kp-serverAuth extended key usage, then
     the certificate MUST include the [Name Constraints
     X.509v3][nameConstraints] extension with constraints on both dNSName and
     iPAddress. For each dNSName in permittedSubtrees, the issuing CA MUST
     confirm that the subordinate CA has registered the dNSName or has been
     authorized by the domain registrant to act on the registrant’s behalf.
     Each dNSName in permittedSubtrees must be a registered domain (with zero
     or more subdomains) according to the [Public Suffix List algorithm][PSL].

     * For each iPAddress range in permittedSubtrees, the issuing CA MUST
       confirm that the subordinate CA has been assigned the iPAddress range or
       has been authorized by the assigner to act on the assignee’s behalf.

     * If the subordinate CA is not allowed to issue certificates with an
       iPAddress, then the subordinate CA certificate MUST specify the entire
       [IPv4][IANA-IPv4] and [IPv6][IANA-IPv6] address ranges in
       excludedSubtrees. The subordinate CA certificate MUST include within
       excludedSubtrees an iPAddress GeneralName of 8 zero octets (covering the
       IPv4 address range of 0.0.0.0/0). The subordinate CA certificate MUST
       also include within excludedSubtrees an iPAddress GeneralName of 32 zero
       octets (covering the IPv6 address range of ::0/0).

     * If the subordinate CA is not allowed to issue certificates with
       dNSNames, then the subordinate CA certificate MUST include a zero-length
       dNSName in excludedSubtrees.

   * If the certificate includes the id-kp-emailProtection extended key usage,
     then all end-entity certificates MUST only include e-mail addresses or
     mailboxes that the issuing CA has confirmed (via technical and/or business
     controls) that the subordinate CA is authorized to use.

10. We recognize that technically constraining subordinate CA certificates as
    described above may not be practical in some cases. All certificates that are
    capable of being used to issue new certificates, that are not technically
    constrained, and that directly or transitively chain to a certificate included
    in Mozilla’s CA Certificate Program MUST be audited in accordance with
    [Mozilla’s CA Certificate Policy][policy] and MUST be publicly disclosed by the
    CA that has their certificate included in Mozilla’s CA Certificate Program. The
    CA with a certificate included in Mozilla’s CA Certificate Program MUST
    disclose this information before any such subordinate CA is allowed to issue
    certificates. All disclosure MUST be made freely available and without
    additional requirements, including, but not limited to, registration, legal
    agreements, or restrictions on redistribution of the certificates in whole or
    in part. The Certificate Policy or Certification Practice Statement of the CA
    that has their certificate included in Mozilla’s CA Certificate Program must
    specify where on that CA’s website all such public disclosures are located. For
    a certificate to be considered **publicly disclosed and audited,** the
    following information MUST be provided:

    * The full DER-encoded X.509 certificate (Each issuing CA should provide
      one .p7c, .zip, or .tgz file containing all of the
      non-technically-constrained intermediate certificates that it has
      signed.);
    * The corresponding Certificate Policy or Certification Practice Statement
      used by the subordinate CA; *and*
    * Annual public attestation of conformance to the stated certificate
      verification requirements and other operational criteria by a competent
      independent party or parties with access to the details of the
      subordinate CA’s internal operations.

11. We consider the criteria for CA operations published in any of the
    following documents to be acceptable:

    * Clause 7, "Requirements on CA practice", in ETSI TS 101 456 V1.4.3 or
      later version, [Policy requirements for certification authorities issuing
      qualified certificates][ETSI-101-456] (only applicable to electronic
      signature certificate issuance; applicable to either the "QCP public" or
      "QCP public + SSCD" certificate policies);

    * Clause 7, "Requirements on CA practice", in ETSI TS 102 042 V2.3.1 or
      later version, [Policy requirements for certification authorities issuing
      public key certificates][ETSI-102-042] (as applicable to the "EVCP" and
      "EVCP+" certificate policies, DVCP and OVCP certificate policies for
      publicly trusted certificates - baseline requirements, and any of the
      "NCP", "NCP+", or "LCP" certificate policies);

    * [ISO 21188:2006][ISO-21188:2006] Public key infrastructure for financial
      services -- Practices and policy framework;

    * WebTrust ["Principles and Criteria for Certification Authorities 2.0" or
      later][WebTrust-2.0] and ["SSL Baseline Requirements Audit Criteria
      V1.1"][WebTrust-BRs] (as applicable to SSL certificate issuance) in
      [WebTrust Program for Certification Authorities;][WebTrust-For-CAs]

    * WebTrust ["Principles and Criteria for Certification Authorities -
      Extended Validation Audit Criteria 1.4" or later][WebTrust-EV] in
      [WebTrust Program for Certification Authorities][WebTrust-For-CAs].

    We reserve the right to accept other criteria in the future.

12. CA operations and issuance of certificates to be used for SSL-enabled
    servers must also conform to version 1.1.5 of the [CA/Browser Forum
    Baseline Requirements for the Issuance and Management of Publicly-Trusted
    Certificates.][CABF] In the event of inconsistency between [Mozilla’s CA
    Certificate Policy][policy] requirements and the Baseline Requirements,
    [Mozilla’s CA Certificate Policy][policy] takes precedence. The items
    listed below will be accepted as reason for not following the Baseline
    Requirements.  If you find an inconsistency that is not listed here, notify
    Mozilla by sending email to certificates@mozilla.org so the item can be
    considered.

    * Mozilla’s CA Certificate Policy defining a competent and independent
      auditor is a superset of section 8.2 of the [CA/Browser Forum’s Baseline
      Requirements][CABF], and takes precedence over it.

13. By "competent party" we mean a person or other entity who is authorized to
    perform audits according to the stated criteria (e.g., by the organization
    responsible for the criteria or by a relevant government agency) *or* for
    whom there is sufficient public information available to determine that the
    party is competent to judge the CA’s conformance to the stated criteria. In
    the latter case the "public information" referred to should include
    information regarding the party’s

    * knowledge of CA-related technical issues such as public key cryptography
      and related standards;

    * experience in performing security-related audits, evaluations, or risk
      analyses; *and*

    * honesty and objectivity.

14. By "independent party" we mean a person or other entity who is not
    affiliated with the CA as an employee or director *and* for whom at least
    one of the following statements is true:

    * the party is not financially compensated by the CA;

    * the nature and amount of the party’s financial compensation by the CA is
      publicly disclosed; *or*

    * the party is bound by law, government regulation, and/or a professional
      code of ethics to render an honest and objective judgement regarding the
      CA.

15. We reserve the right to designate our own representative(s) to act as the
    competent independent party or parties described above, should that prove
    to be necessary and appropriate.

16. The burden is on the CA to prove that it has met the above requirements.
    However the CA may request a preliminary determination from us regarding
    the acceptability of the criteria and/or the competent independent party or
    parties by which it proposes to meet the requirements of this policy.

17. We rely on publicly disclosed documentation (e.g., in a Certificate Policy
    and Certification Practice Statement) and publicly disclosed audit
    statements to ascertain that the above requirements are met. Therefore,
    inclusion requests will only be considered if the following are true:

    * the publicly disclosed documentation provides sufficient information for
      Mozilla to determine whether and how the CA complies with this policy,
      including a description of the steps taken by the CA to verify
      certificate signing requests;

    * the documentation is available from the CA’s official website; and

    * the public attestation of the CA’s conformance to the stated verification
      requirements by a competent independent party indicates which policy
      documents were included in the review.

18. To request that its certificate(s) be added to the default set a CA should
    submit a formal request by submitting a [bug report][bugzilla-CA] into the
    mozilla.org Bugzilla system, filed against the "CA Certificates" component
    of the "mozilla.org" product. Mozilla’s wiki page, [Applying for root
    inclusion in Mozilla products][how-to-apply], provides further details
    about how to submit a formal request. The request must be made by an
    authorized representative of the subject CA, and should include the
    following:

    * the certificate data (or links to the data) for the CA certificate(s)
      requested for inclusion;

    * for each CA certificate requested for inclusion, whether or not the CA
      issues certificates for each of the following purposes within the CA
      hierarchy associated with the CA certificate:

      * SSL-enabled servers, *or*

      * digitally-signed and/or encrypted email;

    * for each CA certificate requested for inclusion, whether the CA issues
      Extended Validation certificates within the CA hierarchy associated with
      the CA certificate *and*, if so, the EV policy OID associated with the CA
      certificate;

    * a Certificate Policy and Certification Practice Statement (or links to a
      CP and CPS) *or* equivalent disclosure document(s) for the CA or CAs in
      question; *and*

    * information as to how the CA has fulfilled the requirements stated above
      regarding its verification of certificate signing requests and its
      conformance to a set of acceptable operational criteria.

    We will reject requests where the CA does not provide such information
    within a reasonable period of time after submitting its request.


19. We have appointed a [CA certificate "module owner"][policy-module] and
    (optionally) one or more "peers" to evaluate CA requests on our behalf and
    make decisions regarding all matters relating to CA certificates included
    in our products. CAs or others objecting to a particular decision may
    appeal to the [Mozilla governance module owner or
    peer(s)][mozilla-governance], who will make a final decision.

This policy applies only to software products distributed by Mozilla,
including the Mozilla Foundation and its subsidiaries.  Other entities
distributing such software are free to adopt their own policies. In
particular, under the terms of the relevant Mozilla license(s) distributors
of such software are permitted to add or delete CA certificates in the
versions that they distribute, and are also permitted to modify the values of
the "trust bits" on CA certificates in the default CA certificate set. As
with other software modifications, by making such changes a distributor may
affect its ability to use Mozilla trademarks in connection with its versions
of the software; see the [Mozilla trademark policy][trademark] for more
information.

Please contact Mozilla at [certificates@mozilla.org][certificates] for more
information about this policy and answers to related questions.

We reserve the right to change this policy in the future. We will do so only
after consulting with the public Mozilla community, in order to ensure that all
views are taken into account.


[policy]: ./index.html
[trademark]: https://www.mozilla.org/en-US/foundation/trademarks/
[certificates]: mailto:certificates@mozilla.org
[CABF]: http://www.cabforum.org/documents.html
[basicConstraints]: http://tools.ietf.org/html/rfc5280#section-6.1.4
[extKeyUsage]: http://tools.ietf.org/html/rfc5280#section-4.2.1.12
[nameConstraints]: http://tools.ietf.org/html/rfc5280#section-4.2.1.10
[PSL]: http://publicsuffix.org/list/
[IANA-IPv4]: http://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xml
[IANA-IPv6]: http://www.iana.org/assignments/ipv6-address-space/ipv6-address-space.xml
[ETSI-101-456]: http://pda.etsi.org/pda/home.asp?wki_id=vXY0eat9Qxoquqxsw%27A2D
[ETSI-102-042]: http://pda.etsi.org/pda/home.asp?wki_id=LJfRMZJQbbbekfdgITkht
[ISO-21188:2006]: http://www.iso.org/iso/iso_catalogue/catalogue_tc/catalogue_detail.htm?csnumber=35707
[WebTrust-2.0]: http://www.webtrust.org/homepage-documents/item54279.pdf
[WebTrust-BRs]: http://www.webtrust.org/homepage-documents/item72056.pdf
[WebTrust-For-CAs]: http://www.webtrust.org/homepage-documents/item27839.aspx
[WebTrust-EV]: http://www.webtrust.org/homepage-documents/item72055.pdf
[bugzilla-CA]: https://bugzilla.mozilla.org/enter_bug.cgi?product=mozilla.org&amp;amp;component=CA%20Certificates
[how-to-apply]: https://wiki.mozilla.org/CA:How_to_apply
[policy-module]: https://wiki.mozilla.org/Modules/Activities#Mozilla_CA_Certificate_Policy
[mozilla-governance]: https://wiki.mozilla.org/Modules/Activities#Governance
