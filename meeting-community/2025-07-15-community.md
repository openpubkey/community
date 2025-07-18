# OpenPubkey Community Meeting

Date: Wednesday, July 16, 2025 - 11:00AM/2:00PM PT/ET

Participants:
- Ethan Heilman (Cloudflare)
- Fabian Kammel

# Agenda

- Nix flake hashes (Fabian)
- Migration to v3 of jwx (Fabian)
- Release v0.8.0 (Ethan)

# Meeting Notes

## Nix flake hashes (Fabian) 
Nix sometimes requires a second commit https://github.com/openpubkey/opkssh/issues/184

Nix flake issues. When a dependency changes, we have to fixup the hash.

There is some Nix support in renovate to handle Nix hashes, but it is flaky and doesn't work well. 

Upstream NixOs Module https://github.com/openpubkey/opkssh/issues/220 If we did this we wouldn't need to manage the flake in opkssh. This sounds good, but each time we do a release we would need to PR new hashes.

What we need for this, is a guide or automation for upstream nix when doing a release.

##  Migration to v3 of jwx (Fabian)

https://github.com/openpubkey/opkssh/pull/261
Library provides implementation of the JOSE ecosystem. Both openpubkey and opkssh use the library. OpenPubkey is using types of that library in its API.

Maintainer seems likely to releasing breaking versions. Maybe it is a good time to revisit the API of OpenPubkey and remove dependency on jwx.

Talking about making things internal in openpubkey.

Remove jwx from interfaces in openpubkey and then from opkssh. Then upgrade to jwx v3.

## Release v0.8.0 (Ethan)

What to put in v0.8.0? 
https://github.com/openpubkey/opkssh/issues?q=is%3Aissue%20state%3Aopen%20milestone%3A%22Release%20v0.8.0%22

Log refactor? Who was working on this? https://github.com/openpubkey/opkssh/issues/213
https://github.com/openpubkey/opkssh/issues/88

Better policy? Debating how much to add auth_id policy. Not in v0.8.0.

Better testing? Needs to happen in OpenPubkey first. Not in v0.8.0.

Debugging OpenID Connect providers? `opkssh login --audit`
Getting to that information, say groups. Not having to do the double base64 decoding. In v0.8.0
https://github.com/openpubkey/opkssh/issues/103

Maybe use this to simplify setting up providers
https://openid.net/specs/openid-provider-commands-1_0.html

Then agents in v0.9.0

# Action Items

- (Fabian) will figure out how to do the upstream release to Nix and disable the Nix flake. Can be done in v0.8.0
- (Fabian) Remove jwx from public interfaces in OpenPubkey and OPKSSH, upgrade to jwx v3. Doesn't need to be v0.8.0
- (Fabian) Refactoring openpubkey, opkssh to use internal.
- (Ethan) Better debugging information for the client in v0.8.0 https://github.com/openpubkey/opkssh/issues/103
- (Ethan) Fix this issue in v0.8.0 https://github.com/openpubkey/opkssh/issues/199
- (Ethan) Get release v0.8.0 out