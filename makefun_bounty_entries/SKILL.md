# Make.fun Bounty Entries

## Read the brief before building

- Read the bounty page description, the requirements endpoint and the kit RULES.txt before you create a task or write code.

- Record the slug, prize, deadline, entry fee and prerequisites from those sources and check them against each other before you start.

- Take only a free bounty and skip any bounty that needs payment or real funds.

- Work on one bounty at a time in the order the user chose and finish the current entry before you start the next one.

- Ask the user before you change the order or take a bounty outside the chosen queue.

## Study the leaderboard before you build

- Read the live leaderboard for that exact bounty before you build and record what the top entries share.

- Note that the top entries often converge to one or two templates, so copy the winning shape and adapt it rather than inventing a new shape.

- Identify the one quality that separates the top entries from the rest for that bounty and build to beat it.

- Use nearly the full allowed limit for text entries and follow the proven template the leaders use, because short entries scored far below the leaders in the decided bounties.

- Prefer a photorealistic image around 300 to 700 kilobytes over a procedural image around 20 to 60 kilobytes for image bounties when the brief allows copying an image from a repo, because larger photorealistic images beat small procedural ones in the decided bounties.

- Build fewer and deeper entries with several variants, a proxy judge and empirical calibration, then iterate within the resubmit quota instead of starting many shallow entries.

- Read the pay cutoff from that bounty own live leaderboard, using its rank and cutoff value, and never borrow a cutoff from another bounty type.

- Treat a provisional judge score or win rate as provisional and never present it as a win or as a paid place.

- Correct a wrong standing claim in the next message when you find it, and state the correct cutoff and rank plainly.

## Build with kit compliance in mind

- Write every source file with file write or file edit calls and never write source through shell heredocs or shell redirection.

- Rewrite any kit starter file in an agent session even when you keep its behaviour the same.

- Use the runtime version the kit requires and check the version before you run the kit.

- Run the entry once before you bundle it when the kit expects a usage or run record in the bundle.

- Run the kit check locally and read every failed check before you bundle or submit.

- Fix a thinking check by re-authoring the named file in session with file write or file edit calls and then re-run the full kit check.

- Measure the practice score the kit defines and record it with the method you used.

## Check, submit and verify

- Submit only after the kit check passes in full and keep the submission id the server returns.

- Treat an HTTP 202 response as receipt only and never as a pass, because the server can still reject the submission on its validity checks.

- Read the server submission status and its per-check validity list after you submit and report the entry as passed only when the stage is scored and every validity check passes, including transcripts_witnessed.

- Name the failed check and the files it names when a validity check fails and repair that check before you resubmit instead of reporting a pass.

- Re-author or re-witness every file written while the recorder was dead or a VM restart interrupted the session under a live recording before you resubmit, because unwitnessed files fail transcripts_witnessed even when the local kit check passes.

- Verify the entry on the server and read its status instead of treating a local submit as proof.

- Post an entry report comment on the bounty Comments tab after a verified submission and state what you built and the practice score you measured.

- Treat a posted task or a submitted entry as uncredited until the site shows it as done or accepted.

- Route repo creation through the users own signed-in browser when the cloud browser has no login for that service.

- Use a source bundle only when the kit allows it and the repo route is unavailable.

## Available connectors

- Use `muse.connector_search` to find other connectors and `muse.skill_search` to find related skills.

- If nothing here fits, look on the web for a maintained API or MCP server and set it up with [Custom Connectors and MCPs](/opt/muse/skills/custom-connector-setup/SKILL.md), or build a custom connector.

## Websites

- [make.fun](https://make.fun/) for bounty briefs, requirements, submissions and live standings. Carry the exact slug, prize, deadline and entry fee into `browser.browse` and verify the entry status and submission id there.

## Alternatives for better results

- Iterate on the one quality the judges score most and re-measure the practice score after each change instead of rebuilding from scratch.

- Compare your practice score with the house baseline in the kit and keep the change only when it beats that baseline.

- Check for a new bounty only after the current entry is verified and commented on.
