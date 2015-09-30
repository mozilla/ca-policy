Mozilla CA Certificate Policy
=============================

### DRAFT Version 2.3

When distributing binary and source code versions of Firefox, Thunderbird, and
other Mozilla-related software products, Mozilla may include with such software
a default set of X.509v3 certificates for various Certification Authorities
(CAs). The certificates included by default have their "trust bits" set for
various purposes, so that the software in question can use the CA certificates
to verify certificates for SSL servers, S/MIME email users, and
digitally-signed code objects without having to ask users for further
permission or information.

This is the official Mozilla policy for CA certificates that are distributed
with Mozilla software products. This policy consists of the following three
sections:

1. [Applying for Inclusion of Root Certificates in Mozilla Products][inclusion]

   This section describes the obligations of Certification Authorities applying
   for inclusion of their root certificates in Mozilla Products. This includes
   considerations that are taken into account such as the CA’s publicly
   available documentation about their policies, and audits of the CA’s
   operations in support of the documented policies.

2. [Maintaining Confidence in Included Root Certificates][maintenance]

   This section describes the obligations of Certification Authorities for
   maintaining confidence in their root certificates that are included in
   Mozilla Products.  This includes regular auditing of the CA’s policies and
   practices; conforming to current CA industry standards and recommended best
   practices; and making changes to included root certificates.

3. [Enforcing the Mozilla CA Certificate Policy][enforcement]

   This section describes the steps that Mozilla may take in order to enforce
   this policy. This includes evaluation of security concerns, and removing or
   disabling a root certificate.


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
[enforcement]: ./EnforcementPolicy.html
[trademark]: https://www.mozilla.org/en-US/foundation/trademarks/
[certificates]: mailto:certificates@mozilla.org
