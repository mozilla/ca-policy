Mozilla CA Certificate Enforcement Policy
=========================================

### (DRAFT Version 2.3)

This section of the [Mozilla CA Certificate Policy][policy] describes the steps
that Mozilla may take in order to enforce this policy. This includes evaluation
of security concerns, and removing or disabling a root certificate.

This is the official Mozilla policy for enforcing the [Mozilla CA Certificate
Policy][policy]:

* When a serious security concern is noticed, such as a major root compromise,
  it should be treated as a security-sensitive bug, and the [Mozilla Policy for
  Handling Security Bugs][security-bugs] should be followed.

* Mozilla may, at its sole discretion, disable (partially or fully) or remove a
  certificate at any time and for any reason. Mozilla will disable or remove a
  certificate if the CA demonstrates ongoing or egregious practices that do not
  maintain the level of service that was established in the [Inclusion Section
  of the Mozilla CA Certificate Policy][inclusion] or that do not comply with
  the requirements of the [Maintenance Section of the Mozilla CA Certificate
  Policy.][maintenance]

* Mozilla will take any steps we deem appropriate to protect our users if we
  learn that a CA has knowingly or intentionally mis-issued one or more
  certificates. This may include, but is not limited to disablement (partially
  or fully) or removal of all of the CA’s certificates from Mozilla’s products.
  A certificate that includes domain names that have not been verified according
  to section 3.2.2.4 of the [CA/Browser Forum’s Baseline Requirements][CABF] is
  considered to be mis-issued. A certificate that is intended to be used only as
  an end entity certificate but includes a keyUsage extension with values
  keyCertSign and/or cRLSign or a basicConstraints extension with the cA field
  set to true is considered to be mis-issued.

* A certificate is disabled by turning off one or more of the three trust bits
  (Websites, Email, Code Signing).  Disablement or removal of a certificate may
  be initiated by submitting a bug report to the mozilla.org Bugzilla system, as
  described in the [Root Change Process][root-change-process] or the [Mozilla
  Policy for Handling Security Bugs][security-bugs].

* If Mozilla disables or removes a CA’s certificate(s) from Mozilla’s products
  based on a CA’s actions (or failure to act) that are contrary to the [Mozilla
  CA Certificate Policy][policy], Mozilla shall publicize that fact in
  newsgroups on the news.mozilla.org server, on Web pages in the www.mozilla.org
  and www.mozilla.com domains, in news releases sent to organizations
  specializing in computer and Internet news, or as an alert to the US-CERT
  organization of the U.S. Department of Homeland Security.

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

[inclusion]: ./InclusionPolicy.html
[maintenance]: ./MaintenancePolicy.html
[policy]: https://www.mozilla.org/en-US/about/governance/policies/security-group/certs/policy/
[trademark]: https://www.mozilla.org/en-US/foundation/trademarks/
[certificates]: mailto:certificates@mozilla.org
[security-bugs]: https://www.mozilla.org/en-US/about/governance/policies/security-group/bugs/
[CABF]: http://www.cabforum.org/documents.html
[root-change-process]: https://wiki.mozilla.org/CA:Root_Change_Process
