# OpenPubkey Community Meeting

Date: Wednesday, Jan 15, 2025 - 9AM/12PM PT/ET

Participants:

- Ethan Heilman (Cloudflare)
- Jonny Stoten
- James Carnegie


# Agenda
1. Working on adding more human OpenID Providers. Starting with adding a web based provider chooser. (Ethan)

2. What OpenID Providers should we add next? I attempted to add RSA corps OP, but ran into difficulties. login.gov? gitlab? azure (definitely)?

# Meeting Notes

- OpenPubkey github does not automatically ping for review when a new PR is created. Ethan needs to look into it.

- Ethan is building a web based OpenID Provider chooser. 

- Discussion about OPK as CLI vs library that people use.

- SSH3 is still live? What's going on there?

- OpenSSF working group conflicts with OpenPubkey meeting. Maybe we should change the meeting. Ben Cotton might be interested? Maybe I should attend that. Change the time for OpenPubkey.

- James: Interesting opportunities for OPK in SPIFFE. major use case in SPIFFE is mutual TLS and scaling bottlenecks. Can you use OpenPubkey to setup mTLS. Linking and cosigning requests if you using JWT, GQ signatures.

Ethan: Checking path through service mesh cosigned by PEP. Replaying JWT concerns.

- Ethan: What should be user OP that isn't Azure.

Jonny: planning on doing the Gitlab user OP (gitlab has a OPK project they are interested). https://github.com/openpubkey/openpubkey/issues/199

- Current supported OPs: google, github-actions, gitlab-ci

OPs we definitely want to support: gitlab (user), Azure

OPs we might want to support: login.gov, twitch, bitbucket, GCP machine identity, salesforce, facebook, linkedin, keycloak, zitadel, Okta

Ethan: The enterprise OPs are tricky because they require configuration

James: Apple OP? https://openid.net/open-letter-from-the-openid-foundation-to-apple-regarding-sign-in-with-apple/ 

Ethan: My personal for coming is getting Azure and Web chooser working. Maybe setting up a prod MFA-Cosigner on AWS lambda or GCP.

James: SPIFEE meeting tommorrow at 10:30 PT 1:30 PM ET (Ethan will try to make it).

Meeting ends at 10:45am (ET).

# Action Items

- Ethan: Fix calendar invite
- Ethan: OpenSSF Supply chain meeting conflict (find new time)
- Jonny: Gitlab OP
- Ethan: Getting Web chooser and Azure working
- James: Report back on SPIFFE and OPK opportunities.
