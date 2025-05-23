# OpenPubkey Community Meeting

Date: Wednesday, May 5, 2025 - 11:00AM/2:00PM PT/ET

Participants:

- Ethan Heilman (Cloudflare)
- Fabian Kammel (control plane)

# OpenPubkey Community Meeting

Date: Wednesday, May 21, 2025 - 11:00AM/2:00PM PT/ET

Participants:

- Ethan Heilman (Cloudflare)
- Fabian Kammel

# Agenda

- Status GHA PR (Fabian)
- Fabian will present his use of opkssh in his homelab (Fabian)
- UserInfo and release 0.7.0 (ethan)


# Meeting Notes

Fabian discusses GHA PR.
Expiration of ID Tokens and GHA, use OIDC expiration policy
Policy controls on GHA https://github.com/openpubkey/opkssh/pull/187#issuecomment-2898851014
What to do about policies more generally
GHA is next to be merged!

Fabian presents his use of opkssh in his homelab
Discussion on piping shell script
Using two different IDPs for opkssh
Maybe opkssh provider add, maybe anisble templates

Ethan talks about userinfo endpoint and opkssh.
Generate claims out of other claims https://kanidm.github.io/kanidm/stable/integrations/oauth2/custom_claims.html
https://github.com/openpubkey/openpubkey/issues/321
https://github.com/firebase/firebase-admin-go/blob/570427a0f270b9adb061f54187a2b033548c3c9e/snippets/auth.go#L295-L308

Ethan will send out userinfo PR for review when finished
