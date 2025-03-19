# OpenPubkey Community Meeting

Date: Wednesday, Feb 19, 2025 - 9AM/12PM PT/ET

Participants:

- Ethan Heilman (Cloudflare)
- Marcel Levy
- Daniel Feldman
- Saahil Bhavsar
- James Carnegie

# Agenda

1. Introductions
2. Demo of Azure and Google working with OPKSSH (Ethan)
3. SPIFFE/SPIRE OpenPubkey

# Meeting Notes

Introductions
James worked with Ethan in the early days with OpenPubkey

Marcel, work at spiral, workload identity, 14 years at AWS, in the PKI space, saw nothing but terrible problems.

Daniel, involved with SPIFFE/SPIRE since the early days. Full time at target, working in their security architecture group

Saahil, graduated college last year, came across OpenPubkey last year, while doing a projecting using Google Auth for authentication

Ethan demos Azure 

Discusses SPIRE/SPIFFE, two proposals, sign the entire HTTP request, similar to AWS seg requests.
Don't force TLS renegotiation
Putting stuff in header
4kb header size limitation

Tracing the user identity through the whole service path

There is a group working on this. There are several groups, transaction token, signing a token for the entire transaction.

https://www.rfc-editor.org/rfc/rfc9421.html 

whimsy standard, adding signatures for intermediaries 

Who should we talk to in whimsy, pieter@spirl.com
Pieter Kasselman would be the person to talk to, Yeran (?)


https://datatracker.ietf.org/doc/draft-schwenkschuster-wimse-credential-exchange/

Which SPIRE ones should I attend, the sig SPIRE

# Action Items


## Action Items from last meeting

* Ethan: Fix calendar invite
* Ethan: OpenSSF Supplychain meeting conflict (find new time)
* Jonny: Gitlab OP
* Ethan: Getting Web chooser and Azure working
* James: Report back on SPIFEE and OPK opportunities.
* 