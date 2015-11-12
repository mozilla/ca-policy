Mozilla CA Certificate Maintenance Policy
=========================================

### (DRAFT Version 2.3)

This section of the [Mozilla CA Certificate Policy][policy] describes the
obligations of Certification Authorities for maintaining confidence in their
root certificates that are included in Mozilla Products. This includes regular
auditing of the CA’s policies and practices; conforming to current CA industry
standards and recommended best practices; and making changes to included root
certificates.

This is the official Mozilla policy for Certification Authorities to maintain
their CA Certificates that are distributed in Mozilla products:

1. CAs are expected to maintain the level of service that was established in the
   [Inclusion Section of the Mozilla CA Certificate Policy][inclusion].

2. CAs must revoke Certificates that they have issued upon the occurrence of any
   of the following events:

    * the subscriber indicates that the original certificate request was not
      authorized and does not retroactively grant authorization;

    * the CA obtains reasonable evidence that the subscriber’s private key
      (corresponding to the public key in the certificate) has been compromised
      or is suspected of compromise (e.g. Debian weak keys), or that the
      certificate has otherwise been misused;

    * the CA receives notice or otherwise becomes aware that a subscriber has
      violated one or more of its material obligations under the subscriber
      agreement;

    * the CA receives notice or otherwise becomes aware of any circumstance
      indicating that use of the domain name in the certificate is no longer
      legally permitted (e.g. a court or arbitrator has revoked a subscriber’s
      right to use the domain name listed in the certificate, a relevant
      licensing or services agreement with the registrant has terminated, or the
      registrant of the domain name has failed to renew it);

    * the CA receives notice or otherwise becomes aware of a material change in
      the information contained in the certificate;

    * a determination, in the CA’s sole discretion, that the certificate was not
      issued in accordance with the CA’s Certificate Policy or Certification
      Practice Statement;

    * the CA determines that any of the information appearing in the certificate
      is not accurate, with the exception of the organizationalUnitName field,
      if present.

    * the CA ceases operations for any reason and has not arranged for another
      CA to provide revocation support for the certificate;

    * the CA private key used in issuing the certificate is suspected to have
      been compromised; or

    * such additional revocation events as the CA publishes in its policy
      documentation.

3. CAs must maintain an online 24x7 repository mechanism whereby application
   software can automatically check online the current status of all unexpired
   certificates issued by the CA. For end-entity certificates:

    * CRLs must be updated and reissued at least every seven days, and the value
      of the nextUpdate field shall not be more than ten days beyond the value
      of the thisUpdate field; or

    * if the CA provides revocation information via an Online Certificate Status
      Protocol (OCSP) service, it must update that service at least every four
      days. OCSP responses from this service must have a maximum expiration time
      of ten days.

4. We require that all CAs whose certificates are distributed with our software
   products provide us an updated statement annually of attestation of their
   conformance to the stated verification requirements and other operational
   criteria by a competent independent party or parties, as outlined in this
   policy. To notify us of an updated statement of attestation, send email to
   [certificates@mozilla.org][certificates] or submit a bug report into the
   mozilla.org Bugzilla system, filed against the "CA Certificates" component of
   the "mozilla.org" product.  The request should include the following:

    * the certificate data identifying the CA certificate(s) to which the
      updated statement of attestation applies;

    * a copy of (or link to) the updated statement of attestation (e.g.,
      "Auditor’s Report and Management Assertions" or equivalent document); and

    * contact information for the party making the attestation, if the statement
      is not posted on an independent website (e.g.  cert.webtrust.org).

5. We require that all CAs whose certificates are distributed with our software
   products notify us when its policies and business practices change in regards
   to verification procedures for issuing certificates, when the ownership
   control of the CA’s certificate(s) changes, or when ownership control of the
   CA’s operations changes. To notify us of updated policies and business
   practices, send email to [certificates@mozilla.org][certificates] or submit a
   bug report into the mozilla.org Bugzilla system, filed against the "CA
   Certificates" component of the "mozilla.org" product.  The request should
   include the following:

    * the certificate data identifying the CA certificate(s) that are affected
      by the change;

    * copies of (or links to) the updated Certificate Policy or Certification
      Practice Statement document(s) or equivalent disclosure document(s); and

    * a summary of the changes that impact the verification procedures for
      issuing certificates.

6. We require that all CAs whose certificates are distributed with our software
   products ensure that we have their current contact information. If the CA’s
   primary representative for their included root certificates leaves the
   organization, then the burden is on the CA to inform Mozilla of the contact
   information for the new primary representative, by sending email to
   [certificates@mozilla.org][certificates].  If we are not able to contact a
   CA, or do not have current audit and policy documentation, then the CA’s root
   certificates may be disabled or removed as described in the [Enforcement
   Section of the Mozilla CA Certificate Policy][enforcement]

7. A failure to provide required notifications or updates as specified in items
   \#4, \#5, and \#6 in a timely manner shall be grounds for disabling a CA’s
   root certificates or removing them from Mozilla products. For this policy "a
   timely manner" means within 30 days of when the appropriate data or
   documentation becomes available to the CA.

8. We consider the following algorithms and key sizes to be acceptable and
   supported in Mozilla products:

    * SHA-1 (until a practical collision attack against SHA-1 certificates is
      imminent);

    * SHA-256, SHA-384, SHA-512;

    * Elliptic Curve Digital Signature Algorithm (using ANSI X9.62) over SECG and
      NIST named curves P-256, P-384, and P-512;

    * RSA 2048 bits or higher; and

    * RSA 1024 bits (only until December 31, 2013).

9. We expect CAs to maintain current best practices to prevent algorithm attacks
   against certificates. As such, the following steps will be taken:

   * software published by Mozilla will return an error
     when a certificate with an MD2, MD4, or MD5-based signature is used;

   * software published by Mozilla will return an error when the
     SSL/TLS certificate has an RSA key size smaller than 2048 bits; and

   * all new end-entity certificates must contain at least 20 bits of
     unpredictable random data (preferably in the serial number).

10. Changes may be made to root certificates that are included in Mozilla
   products as follows:

    * root changes that are motivated by a serious security concern such as a
      major root compromise should be treated as a security-sensitive bug, and
      the [Mozilla Policy for Handling Security Bugs][security-bugs] should be
      followed;

    * enabling a trust bit in a root certificate that is currently included, may
      only be done after careful consideration of the CA’s current policies,
      practices, and audits, according to the [Inclusion Section of the Mozilla
      CA Certificate Policy][inclusion], and may be requested by a
      representative of the CA or a representative of Mozilla by submitting a
      bug report into the mozilla.org Bugzilla system, as described in Mozilla’s
      wiki page, [Applying for root inclusion in Mozilla
      products][how-to-apply-trust-bits];

    * enabling EV in a root certificate that is currently included, may only be
      done after careful consideration of the CA’s current policies, practices,
      and audits, according to the [Inclusion Section of the Mozilla CA
      Certificate Policy][inclusion], and may be requested by a representative
      of the CA or a representative of Mozilla by submitting a bug report into
      the mozilla.org Bugzilla system, as described in Mozilla’s wiki page,
      [Applying for root inclusion in Mozilla
      products][how-to-apply-trust-bits];

    * disabling a root is the act of turning off one or more of the trust
      bits (Websites, Email), and may be requested by a
      representative of the CA or a representative of Mozilla by submitting a
      bug report into the mozilla.org Bugzilla system, as described in the [Root
      Change Process][root-change-process];

    * a representative of the CA or a representative of Mozilla may request that
      a root certificate be removed by submitting a bug report into the
      mozilla.org Bugzilla system, as described in the [Root Change
      Process][root-change-process].

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
[inclusion]: ./InclusionPolicy.html
[maintenance]: ./MaintenancePolicy.html
[enforcement]: ./EnforcementPolicy.html
[trademark]: https://www.mozilla.org/en-US/foundation/trademarks/
[certificates]: mailto:certificates@mozilla.org
[security-bugs]: https://www.mozilla.org/en-US/about/governance/policies/security-group/bugs/
[how-to-apply-trust-bits]: https://wiki.mozilla.org/CA:How_to_apply#Enable_Additional_Trust_Bits_for_an_included_root
[root-change-process]: https://wiki.mozilla.org/CA:Root_Change_Process
