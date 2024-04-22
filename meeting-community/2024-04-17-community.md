# OpenPubkey Community Meeting

Date: Wednesday, April 17, 2024 - 9AM/12PM PT/ET | [Google Meet Link](https://meet.google.com/oom-qgcz-wsy)

Participants:
* Ethan Heilman (BastionZero)
* Joel Kamp (Docker)
* David Dooling (Docker)
* Ann Ming Samborski (BastionZero)

# Agenda
1. [PIKA](#pika) 
2. [JKT in PK Tokens](#jkt-in-pk-tokens)
3. [GQ JWT RFC](#gq-jwt-rfc)
4. [Supporting zkSnarks](#supporting-zksnarks)
5. [SSH3](#ssh3)
6. [Any Other Business (AoB) and Questions](#any-other-business-aob-and-questions)
7. [Action Items](#action-items)

# Meeting Notes

## PIKA

Conversation led by Ethan Heilman.

See the PIKA draft [here](https://www.ietf.org/archive/id/draft-barnes-oauth-pika-00.html). This was originally called Durable OP Keys and has evolved to Proof of Issuer Key Authority (PIKA).

Broadly covering the benefits:
- Redistribute keys without having to go to JWKS URI (good for offline systems or other processes that don't use the Internet).
- TLS keys that sign JWS can be changed all the way up to the CA roots (which we know are changed approximately once every 40 years or so). Based on that long timeline, you can determine if a JWK was in an OP's JWKS URI well into the future.
- The current draft proposal is [here](https://www.ietf.org/archive/id/draft-barnes-oauth-pika-00.html). If you think this is useful and would be valuable, it would be a great help if you would write an email with your support on the IETF thread [here](https://www.mail-archive.com/oauth@ietf.org/msg23240.html).

## JKT in PK Tokens

Conversation led by Ethan Heilman.

Key questions that prompted this topic: 
1. Should JKT live in the GQ header?
2. Should our GQ library require them for GQ JWT?

- OIDC doesn't require public keys to have key ids.
- It is suggested that you do if you have more than one public key, but there isn't a hard requirement, and you can recycle `kids` (key ids) so there's no guarantee of uniqueness.
- When we produce a PK Token, we associate a JSON Key Thumbprint (JKT) with it  (currently, it is included as a public unsigned header).
- As we move towards a more compact representation of the PK Token, we need to decide how to handle PKT because the compact representation does not allow unsigned data.
- QUESTION: How do we get the JSON Key Thumbprint into the compact PK Token?
- Could we, for now, include it in the protected GQ Signature header?

## GQ JWT RFC?

Conversation led by Ethan Heilman.

Rolling in from the previous topic, Ethan raised the idea of standardizing how we use GQ JWT. 

- If you had a standard for GQ JWT, you would very likely want JKT to be in the header.
- Would it make sense to write an RFC around this topic for the use case of wanting to store a JWT with the risk of it being replayed removed?
- It may make more sense to include this as a ZK Proof. We want to make parts of the JSON Web Token available selectively without any risk of replay.
- What would our common standard look like?
- Perhaps zkSnarks on JWTs, use ZK Login and Risk0 to interact. 
- Can we broaden the way we think about GQ, zkSnarks, etc.? There are many different algorithms we can use with JWTS to prevent replay attacks, and for now, we are starting with GQ.

## Supporting zkSnarks

Conversation led by Ethan Heilman.

- The `v 0.5.0` release of OPK will be privacy focused. In particular, we are looking to support zkSnarks with this release.
- Question from Ethan: To ensure that OPK works with all the major OPs, what's the best way to go about this? One approach is using zk login, which supports JWTs but relies on the nonce. Another is Risk0, which is compatible with Rust code. Risk0's runtime is slightly slower than zk login.
- Answer from Joel: Let's use both. We can provide the fastest experience for Google OP using zk login and still be compatible with other OPs via Risk0.

## SSH3

Conversation led by Ethan Heilman.

- OPK is ~1 PR away from where we'll need to be to start thinking about SSH3 support.
- Ethan to spend next few days getting that PR into our repo. 
- Ethan plans to incorporate the auth module that's currently a draft PR coming from the SSH3 team. 

## Any Other Business (AoB) and Questions

Call for assistance: if anyone has experience with submitting a PR to OpenSSH, please send us a note!

# Action Items

No action items were generated from this community meeting.
