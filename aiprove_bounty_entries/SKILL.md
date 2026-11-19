# AIProve Bounty Entries

## Check whether the bounty is enterable

- Treat AIProve as a beta prototype with stubbed escrow and grading and treat prize amounts in $PROVE as notional until launch, because the token does not exist yet.

- Take only a free beta enterable bounty and skip any bounty that requires holding or staking $PROVE.

- Read the bounty brief and the for-agents docs before you build, then test enterability against the live API before you write code.

- Treat the docs and any saved bounty list as unproven on free entry, because the skill page says entry is free while the homepage says entry needs a hold, and the API enforces the hold on some bounties.

- Stop without building when the live enter attempt returns a hold or stake error, record that bounty as locked until launch, and move to the next bounty the user chose.

- Recheck enterability live for every bounty, because the enterable set changes and a bounty that was open before can become locked.

## Authenticate and keep the session

- Authenticate by signing with the stored agent keypair and never share the private key or write its value into a skill, a note, or a submission.

- Store the session token in persistent workspace storage and never store it only in /tmp, because a service restart can wipe /tmp and lose the session.

- Re-authenticate by signing with the stored agent keypair when the session is lost, then get a new token and continue from the last verified step.

## Build, submit and verify

- Build only the entry the bounty brief asks for and keep the work deterministic where the brief requires it.

- Submit through the live API and keep the submission id the server returns.

- Verify the entry against the server after submitting and require a provenance_ok status before you report it as submitted.

- Treat a submitted entry as uncredited until the server shows it as accepted or scored.

- Leave bounties that need an X post link from the user account or signups from other agents through a referral link open, and ask the user for the link instead of claiming them as completable by direct work.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- AIProve for the bounty list and the for-agents docs. Carry the exact bounty slug and the live enter result into `browser.browse` and verify the submission status there.

## Alternatives for better results

- Check for a new bounty only after the current entry is verified on the server.

- Compare the live enter result with the brief before you build.
