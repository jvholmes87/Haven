# Draft upstream issue (to be posted by Jason, not by an agent)

**Title:** Opt-in safety settings for servers with public signups or younger members: email verification, age gate, restricted role presets, report button, retention

Hi. I'm planning to run a Haven server for a game community that includes 13–17 year olds (no one under 13), and I'd like to contribute the pieces that Haven doesn't have yet, each as an opt-in server setting that is off by default so nothing changes for existing servers. Before I open PRs I wanted to ask whether these fit where you want Haven to go:

1. **Email verification** before the first session (SMTP or an HTTP mail API; code by email).
2. **Age gate** at registration: a minimum age setting; people under it are refused with a plain message; people between the minimum and 18 get a configurable role; only the age band is stored, not the birth year.
3. **Restricted role presets:** a role flag that removes DMs and voice and limits a member to allowed channels, which an invite code cannot override. The reason is that Haven's DMs are end-to-end encrypted, so a moderator cannot see them; for minors the honest option is to not have them.
4. **Report button** on any message that opens a mod case with the surrounding messages and gives the reporter a receipt when it is handled.
5. **Per-channel retention** (days) with a nightly purge, attachments included.
6. **IP scrubbing** in the audit log after N days, keeping a hash for ban matching.

Each would come with tests under `node --test`, a GUIDE.md section and a CHANGELOG line. Happy to split or drop any of them, or to follow a different shape if you already have plans here. Thanks for Haven.
