# OpenPubkey Community Meeting

Date: Wednesday, December 20, 2023 - 9AM/12PM PT/ET | [Google Meet Link](https://meet.google.com/oom-qgcz-wsy)

Participants:
* Lucie Mugnier (BastionZero)
* Ethan Heilman (BastionZero)
* Mike Milano (BastionZero)
* Joel Kamp (Docker)
* Justin Cappos (NYU/TUF/in-toto)
* Sharon Goldberg (BastionZero)
* David Dooling (Docker)

# Agenda
1. [Draft Proposal for Historical Logs of OIDC Signing Keys](#draft-proposal-for-historical-logs-of-oidc-signing-keys)
2. [Protocol Process Standardization](#protocol-process-standardization)
3. [Version 1 Update](#version-1-update)
4. [Additional Use Cases](#additional-use-cases)
5. [Any Other Business (AoB) and Questions](#any-other-business-aob-and-questions)

# Meeting Notes

## Draft Proposal for Historical Logs of OIDC Signing Keys
Presented by Sharon Goldberg

Sharon Goldberg is working with Richard Barnes on a draft to the IETF priority because there are competing standards. A standard for OPs to maintain a historical signing log for their long-lived keys. Something for now and OPK and for verifying credentials.

The approach requires redistributability and history. 
* Use the "x5c" (X509 certificate) field in JWKS. 
* Take a certificate chain, convert to bits and stuff into jwks endpoint. 
* Web PKI certificate chain, where the leaf certificate is pub key used to sign off on op key. Use web pki to validate op's signing key but currently bound by current lifetime (~90 days). hash chain, new key has hash of older key sets. validate using old tls certificate. problem: old keys may not be safe. open to thoughts or feedback.

Justin Cappos: How do you know the new key is allowed to sign the old key?

Sharon Goldberg: OP key or TLS key? OP keys are the things being signed.

Ethan Heilman: JWKS key is signed by current tls cert attests to all past keys. TUF attempts to have no dependencies on TLS, but this proposal does.

Sharon: Same root of trust (TLS) to have keys signed by old keys. Does OPK/OIDC depend on TLS?

Ethan: Currently, OIDC depends on TLS for delivery of keys.

Sharon: JWKS is accessed via HTTPS. Is that cool?

Justin: For TUF, the concern was that any server with internet access is historically risky. Reasonable assumption for OPK use case.

Ethan: SUI attets to validity state of JWKS URIs. But they're a blockchain. TLS requirement would not work for them. Maybe we use TLS and an additional method for determining validity outside of TLS.

Sharon: Why is old signs new good?

Justin: For non-sensitive data new signs old is fine, but to protect against compromise, we have found old signs new to be the best approach.

----

Notes from Justin Cappo: 
TAP a proposal attempting to solve the same problem. The Archive Framework (TAF) layers a git repository into TUF to answer the question of what did it think was current when it was established. 

TAF: https://github.com/openlawlibrary/taf  (their docs are hard to follow, ask me if you have any questions / thoughts)

TAP 8 discussion issue with links to actual text, etc. We have a more up-to-date version of this we are publishing / prototyping now, but the cure is essentially the same. 

We may end up splitting out the self-revocation and rotation into separate TAPs. Marina Moore is the right person from our side to talk with.

https://github.com/theupdateframework/taps/issues/37

----

## Protocol Process Standardization
Presented by Ethan Heilman
Reference document: https://docs.google.com/document/d/14vN6uNFSJJ1EyINmgKwsIdy5-zQmEpfqfsjIlwTnq_M

Ethan presented proposal in document specifically requested feedback on OpenPubkey Improvement Proposal (OIP).

## Version 1 Update
Presented by Ethan Heilman

V1 is stable interface for producing simple "getting starting" instructions for developers. Arch will change but will change at slower rate. Somewhat stable interface and architecture for the client and verifier. 

2 open questions from previous meeting:

**How do deal with OPs that don't have "kid"s?** Resolved in PR.

**What changes need to be made to the client to support OP pub keys after they rotate?** Still open question. James had a PR to address this that he closed.
* Ethan: Not a v1 requirement because there's no clear proposal that has been set out. But a question for Jonny and James.
* Joel: Agrees not necessary for v1.

Where we are with v1:
* Moved v1 label to milestone
* Documentation after we declare v1

Main remaining tasks:
1. PK token validation object (solves most tasks)
2. gq256 signature algorithm specification ([PR#66](https://github.com/openpubkey/openpubkey/pull/66))

# Additional Use Cases
Ethan: SUI blockchain, inspired by OpenPubkey is using a pktoken structure similar to our own, uses smart contracts to attest to the state of JWKS endpoints. Take ID token and use zero knowldge proof using SNARKs. Zero knowledge proof takes 2 seconds on a server but 10 seconds on a client. They've had a full, professional crypto audit.

# Any Other Business (AoB) and Questions
Justin Cappos: Are we using transparency logs for solving OIDC provider key rotation?
Joel Kamp: Has a [PR](https://github.com/openpubkey/signed-attestation/pull/4) using rekor. 

# Action Items
No action items were generated from this community meeting. 