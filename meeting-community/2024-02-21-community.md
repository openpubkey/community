# OpenPubkey Community Meeting

Date: Wednesday, February 21, 2024 - 9AM/12PM PT/ET | [Google Meet Link](https://meet.google.com/oom-qgcz-wsy)

Participants:
* Ethan Heilman (BastionZero)
* Lucie Mugnier (BastionZero) 
* Ann Ming Samborski (BastionZero)
* Jonny Stoten (Docker)
* Richard Barnes (Cisco)
* Ben Cotton (Docker)
* Joel Kamp (Docker)
* Sharon Goldberg (BastionZero)
* Victor Lu

# Agenda
1. [Fireside Chat Reminder](#fireside-chat-reminder)
2. [OpenPubkey Archival JWK Sets: SUI Demo](#openpubkey-archival-jwk-sets)
3. [zkLogin Private OIDC Tokens in OpenPubkey](#zklogin-private-oidc-tokens-in-openpubkey) 
4. [GitLab Support](#gitlab-support)
5. [Durable OP Key Draft](#durable-op-key-draft)
6. [Issues With Memguard](#issues-with-memguard)
7. [Additional Use Cases](#additional-use-cases)
8. [Any Other Business (AoB) and Questions](#any-other-business-aob-and-questions)

# Meeting Notes

## Fireside Chat Reminder

Our very own Ethan Heilman, Ben Cotton, and Michael Irwin held a fireside chat on LinkedIn on Wednesday, 21 February 2024. For those who could not make it, you can watch the session [here](https://www.linkedin.com/events/7160671049448046592/about/).

## OpenPubkey Archival JWK Sets

Presented by Ethan Heilman. See the proposal discussed [here](https://github.com/openpubkey/openpubkey/pull/102). 

R. Barnes: What protection is there for protecting against asserting a key from Google that Google never actually provided?

E. Heilman: SUI's blockchain attests to when the key was first used. Although I would love an alternative option. SUI wants a set of trusted parties w/ economic value at stake, but for many projects, establishing whether or not the JWK is right or not may be a non-starter due to project constraints. Outside more of an auditing functionality, this may not be something people are interested in incorporating. 

L. Mugnier: If a key is known to be compromised, how does revocation work?

E. Heilman: If a key is revoked, they'd need to handle it in the blockchain. You can't interact with smart contracts with new signatures. If they remove it, then you can't sign any new things. Plus they have timestamping so you can't go back to change history unless you do some nefarious things. 

For archival JWKS, this probably needs to handle it at the verifier level.

R. Barnes: Is the authority provided for keys or only for the objects that are providing those keys? If OP key is active from time 0 to time N, how do you guard against compromise of that key far in the future, allowing the attacker to mint objects that are issued during that time period but were actually created far in the future once that key was compromised? How do you know it was created during the real timeframe?

E. Heilman: Based on his knowledge of SUI, signatures are timestamped on the blockchain so you can validate when that happens. 

R. Barnes: Sounds like SUI has handled this, but it is worth noting that this lookback assurance requirement is carried forward into anything that we design for OPK. 

## zkLogin Private OIDC Tokens in OpenPubkey

Presented by Ethan Heilman. See the issue discussed [here](https://github.com/openpubkey/openpubkey/issues/101). 

It seems we could transform objects they provide us into a PK Token allowing us to provide privacy for PK Token and enabling people to reveal selectively the contents of their claims.

## GitLab Support

Presented by Ethan Heilman.

In the interest of time, Ethan asked folks to review his proposal offline and leave comments. It's [issue no. 100](https://github.com/openpubkey/openpubkey/issues/100).

## Durable OP Key Draft

Presented by Sharon Goldberg and Richard Barnes. See the comment-enabled draft [here](https://docs.google.com/document/d/1RJzq17VOhSwhuzLzcwZx7-yvlgjOsWubM7NgjfMV5ug/edit?usp=sharing).

This is a draft of how you can modify OPs for applications like the Docker signing use case where you may have a long-lived signature that relying parties would want to verify quite a long time after the OP key was rotated. Additionally, Richard added that he's interested in VC because we want to use them for end-to-end identity in Webex.

The intent is to propose this change to OPs.

J. Kamp: Is that based on whenever their signing certificate expires?

S. Goldberg: Not quite. They can refresh their certificate - the key can be valid for a longer window that the web PKI certificate, and the OP can issue a new object if needed. Based on current standards, the web PKI certificate is supposed to be rotated every 90 days.

L. Mugnier: Is there any cadence associated with OPs with this model?

R. Barnes: Signed OP key structs that we have states all 6 of the timeframes. Whenever you issue a new statement that a key is valid for verifying, you can change the interval that you can say the key was valid for signing so that isn't something that this proposal guards against.

E. Heilman: Do we think people would be willing to trust CT logs?

## Issues With Memguard 

We did not get a chance to cover this [issue](https://github.com/openpubkey/openpubkey/issues/103) during the hour and will make sure it's covered in the next meeting!

# Additional Use Cases

No additional use cases beyond what was discussed above were raised during this community meeting. 

# Any Other Business (AoB) and Questions 

* Ethan to book a follow up meeting to continue the discussion on the Durable OP Key draft. Stay tuned on [Slack](https://openssf.org/getinvolved/) in the `#openpubkey` channel.

# Action Items

No action items were generated from this community meeting.
