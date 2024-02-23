# OpenPubkey Community Meeting

Date: Wednesday, January 17, 2024 - 9AM/12PM PT/ET | [Google Meet Link](https://meet.google.com/oom-qgcz-wsy)

Participants:
* Trishank Karthik Kuppusamy (Datadog)
* Marina Moore (NYU)
* Lucie Mugnier (BastionZero)
* Ethan Heilman (BastionZero)
* Jonny Stoten (Docker)
* Joel Kamp (Docker)
* Ann Ming Samborski (BastionZero)

# Agenda
1. [SUI JWKS Oracle and ZK Tokens](#sui-jwks-oracle-and-zk-tokens)
2. [Additional Use Cases](#additional-use-cases)
3. [Any Other Business (AoB) and Questions](#any-other-business-aob-and-questions)

# Meeting Notes

## SUI JWKS Oracle and ZK Tokens

Discussion led by Ethan Heilman

[SUI](https://sui.io/)
- Offers a signed, attested chain of history of public keys (i.e., all of Google's pubkeys).
- Ethan has a script they provided him that extracts all keys from the chain of public keys. He would like to create a demo that shows the validation of PK Tokens and signed messages using SUI as the oracle for historic pubkeys. 
- Main goal: develop a pattern for OPK to follow for integrating other historical pubkeys in the future.
- SUI also uses id tokens and uses zero-knowledge (ZK) proofs in their CIC. 
- Ethan will put together a PR that proposes a way for OPK to support ZK-proof friendly nonce commitments.

Question: Any concerns or thoughts around that approach?
- Joel Kamp: Prefers something blockchain distributed, then they cannot retroactively change the keys from the past. Ideally, this would be integrated with the IdP so you can see more information about the key itself (when it was valid, was it revoked, was it rotated for routine security measures).
- Trishank Karthik Kuppusamy: You could add TUF metadata to a blockchain: https://ssl.engineering.nyu.edu/blog/2020-02-03-transparent-logs.

Question from Trishank: Why is TUF being used? 
- For the Docker signing solution, TUF maps identities -> policies. Public key log is to mitigate the problem of rolling public keys from OIDC providers (this can be considered a secondary use case).

Question from Ethan: Can you put a transparency log inside of a TUF? 
- Trishank: Yes, doesn't see a reason why you couldn't. 
- Ethan: It would be nice to have a transparency log outside of the TUF because you get all the ordering and when you verify, you can see if there is something wrong with the TUF.

Question from Jonny: Ethan, can you elaborate more on your vision for using a ZK-friendly nonce? 
- Ethan: I'll write up an issue before putting out a PR with more detail. If we support ZK-SNARK (Zero-Knowledge Succinct Non-Interactive Argument of Knowledge), we likely want to also support a ZK-friendly hash function. 

Question from Joel: Do we know if any ZK proof algorithms are being reviewed by NIST presently?
- Ethan: I'm not sure, but I think it's a topic of interest. NIST + SUI had had some of those discussions. My sense is that a lot of the identity standards that will come out in the future will be ZK-based.

Question from Ethan: Do folks have thoughts around letting users set their own expiry time vs. externally set?
- Marina: No major issue from me as long as there is an upper bound. It's helpful if the user is able to communicate that they will lose the key in 5 minutes. 

Additionally, the following were mentioned in passing for future consideration:  
- DEX: uses anonymized fields (federation layer b/t identity providers).
- Fulcio: submit a PK token, and they could transform it into a SNARK that they would sign.

# Additional Use Cases
No additional use cases were raised during this community meeting. 

# Any Other Business (AoB) and Questions 

# Action Items
No action items were generated from this community meeting.