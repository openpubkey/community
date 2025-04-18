# OpenPubkey Community Meeting

Date: Wednesday, April 16, 2025 - 11:00AM/2:00PM PT/ET

Participants:

- Ethan Heilman (Cloudflare)
- Johannes (net42)
- Fabian Kammel (control plane)
- Naveen Siddareddy

# Agenda

- v0.5.1 of opkssh is out, update, test, open issues. Static linking should fix alot. (Ethan)
- Create mailinglist for announcements and discussion (Ethan)
- Integration tests taking 5 minutes to run, anyone know how to make them go faster? (Ethan)
- Client config file (Ethan)
- oidc:group support in v0.4.0 (Fabian)
- claim debugging in opkssh CLI (Fabian)
- moving opkssh keys from the default .ssh directory (Johannes)
- access token and group claims not in the ID Token/userinfo (Ethan)


# Meeting Notes

Ethan: Announcement list to reach people using and depending on openpubkey. Probably go with google groups. Put in the top of the readme, bsky, twitter, etc... anywhere else?

Ethan: Integration tests are talking longer and longer to run

Fabian: I'd take a look.

Ethan: Client config file, biggest usability problem is custom specifying providers.

Fabian and Johannes: that would be helpful

Fabian: CLI should support all the actions to edit it. So for the UX on the CLI side.

Johannes: The definition where I want to place my files for client config. Where to place them or to instruction ssh agent to load them instantly.

Fabian: oidc:group support in v0.4.0 
Did try to setup it, ran into multiple issues, but works on main.
A bit annoying to figure out, what can is actually in the JWT. I had to manually base64 decode it twice.

It would be nice if the CLI had support for printing out information about the certificate that was issued.

Ethan: Here is the base64 blob, dump it

Fabian: Something on client that prints out the certificate and all claims.

Fabian: I'll put my notes into a PR

Ethan: Really annoying that google does not put group claims in ID Tokens.

Naveen Siddareddy: Opa approach, ... not dealing with groups

Ethan: Policy Commands should let you do it?

Johannes: We wasted a few hours with the issued at offset. Key cloak and I think the default value is 1 min expiration.

Fabian will present his use of opkssh in his homelab at the next opkssh community meeting