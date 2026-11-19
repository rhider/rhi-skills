# Bug Hunting and Security Review

## When to use this skill

- Use this skill when the user asks you to find security bugs, review code for vulnerabilities, test an application, or write up a security finding.

- Use it for defensive review of the user's own code and for authorized bug bounty targets and AIProve bug hunt bounties.

- Never use it against a target the user does not own and has no written authorization to assess.

- The per-class pattern library lives in the Claude-BugHunter bundle: clone https://github.com/elementalsouls/Claude-BugHunter and read the matching `hunt-*` skill under its `skills/` directory before you test a specific class.

## Confirm the mode first

- State the engagement type as the first line of your notes before you touch any tool.

- For a bug bounty, only impact-demonstrated bugs count, so hygiene alone is not a finding.

- For a red team engagement, hygiene findings plus recon plus defensive observations are all deliverables.

- For a pentest, read the statement of work and follow its scope exactly.

- For defensive review of the user's own code, the finding is a defect to fix, so report the root cause plus the concrete fix.

- If you cannot answer the mode from the user's instruction, ask once and do not assume.

## Run the five phase workflow

- Work through recon, mapping, discovery, proving and reporting, and move freely between phases when you get stuck.

- In recon, maximize the attack surface first and rank it before you test anything.

- In mapping, learn the app the way its developer does and note auth models, roles and business critical flows.

- In discovery, pick one or two vulnerability classes per session and test only those.

- In proving, chain the finding to real harm and minimize the prerequisites an attacker needs.

- In reporting, run the seven question gate first and write only what passes it.

- When you find a critical in the first thirty minutes, stop recon, validate it fully, report it, then return to recon.

## Apply the seven question gate

- Ask these seven questions in order before you write any report and kill the finding at the first wrong answer.

- Write the exact HTTP request that uses the bug right now and the exact data it reads, modifies or deletes.

- Check that the impact sits on the program accepted impact list and that the root cause is in an in-scope asset.

- Check that the bug does not need privileged access an attacker cannot realistically get.

- Check that the behaviour is not already known or accepted by design.

- Prove impact beyond technically possible by showing real data, a real session or real money, not an error message alone.

- Check that the bug class is not on the never submit list, which includes missing security headers alone, self XSS, open redirect alone, logout CSRF and DNS only SSRF.

- Run the pre severity gate before you label anything Critical or High and answer what the attacker walks away with in one concrete sentence.

## Kill false positives with discipline rules

- Use a random marker of eight or more characters with no English words when you test for reflection or out of band callbacks, and check the baseline response for the marker before you claim a hit.

- Demand a response body difference before you claim a bypass, because a 200 status with a byte identical body is not a bypass.

- Require at least ten interleaved trials per group before you claim any timing based signal, and demand the suspect mean sit at least two standard deviations above the control mean.

- Never infer an auth bypass from a validation error, because a global input sanitizer often runs before the auth middleware, so retest with a minimal well formed body and only trust the answer that body gets.

- Use Python with a try block per iteration for any loop over five items, because shell loops can silently skip work.

- Reproduce a Critical or High finding with at least two independent tools before you report it.

## Use the per-class pattern library

- Read the bundle's `skills/bb-methodology/SKILL.md` at the start of any hunting session for the full workflow and thinking framework.

- Read the bundle's `skills/triage-validation/SKILL.md` before you write any report for the seven question gate, the four pre-submission gates and the never submit list.

- Read the matching `hunt-*` skill for the class you test, such as `hunt-xss`, `hunt-sqli`, `hunt-ssrf`, `hunt-idor`, `hunt-auth-bypass`, `hunt-jwt-crypto`, `hunt-oauth`, `hunt-graphql`, `hunt-race-condition` or `hunt-file-upload`.

- Read the bundle's `skills/redteam-mindset/SKILL.md` when a defended target keeps blocking you, because it teaches continuation discipline instead of early stopping.

- Read the bundle's `skills/evidence-hygiene/SKILL.md` before you capture proof screenshots or HTTP logs, because it covers redaction of cookies and personal data.

- Read the bundle's `skills/report-writing/SKILL.md` when you draft the report for the platform format and title formula.

## Tooling

- Install the recon and scanning tools you need (subfinder for subdomains, trufflehog for secret scanning, nuclei with nuclei-templates for template scanning, SecLists wordlists, PayloadsAllTheThings payloads, HackTricks methodology, nomore403 for 403 bypass testing, turbo-intruder as a Burp Suite extension for race conditions) and keep an inventory of versions.

- For recon use subfinder to enumerate subdomains of an in-scope target.

- For secret scanning use trufflehog against the user's own repositories and directories.

- For template based scanning use nuclei with the nuclei-templates.

- For payloads per bug class read PayloadsAllTheThings.

- For wordlists use SecLists with Discovery, Passwords, Fuzzing and Usernames checked out.

- For pentest methodology read HackTricks.

- For 403 bypass testing use nomore403.

- For race condition testing use turbo-intruder, which only runs as a Burp Suite extension.

- Run every tool only against the user's own code or a target with written authorization, and never against an external target without it.

## Write the report impact first

- Before you write, run the pre-writing checks: read the program scope and rules and confirm the bug is in scope; check disclosed reports and the changelog for duplicates; test safely on your own account, never touch another user's data, avoid denial of service; re-verify the finding so it is not a false positive.

- Structure the report in eight sections: title, summary, severity, reproduction steps, proof of concept, impact, fix recommendation, additional info.

- Title the finding with the bug class, the endpoint and the impact in one line. Bad: "XSS di website". Good: "Stored XSS di kolom komentar /posts/{id} memungkinkan pengambilalihan sesi".

- Put the impact in the first sentence of the summary and state exactly what the attacker can do, in two or three sentences: what the bug is, where it is, what follows from it.

- Score severity as Low, Medium, High or Critical with a CVSS 3.1 score and the reasoning behind it, matching the actual impact, never the theoretical one. Do not inflate it; credibility is the stake. Severity calibration example: a real triage rated a P2P ban-score bypass Low because no harm to the node was demonstrated — each request was bounded and inexpensive, the attacker had to keep sending requests to sustain any load, and there was no crash, resource growth, consensus impact or loss of funds.

- Give copy-pasteable steps to reproduce with the exact HTTP request. This is the most important section: URL, endpoint, parameters, method, account, payload and starting conditions, step by step, so the triager can repeat the bug.

- Attach proof of concept: a screenshot, a short video or a minimal script. Redact sensitive data. Prove the impact without causing damage.

- Describe impact as a realistic scenario: who is affected, what data is reachable, what the attacker can do. Do not speculate wildly. Focus on business impact: account takeover, data leak and remote code execution are usually rated highest.

- Give one or two sentences of concrete remediation, such as input validation, output encoding, server-side authorization checks or rate limiting. It is optional but teams like it.

- Add additional info: test environment, date and time, and CWE or OWASP references.

- Keep the report under 600 words and never write "could potentially" or "may allow" in it.

- Acceptance tips: one report holds one bug, unless you chain bugs and explain the chain; use professional, neutral language and never demand a bounty at the start; stop exploiting once the proof is sufficient; answer clarification requests fast and politely; follow the disclosure policy and never publish before you are allowed to.

- Common mistakes that get reports rejected: a generic title, ambiguous reproduction steps, scanner output reported without verification, inflated severity, out-of-scope or known issues, and duplicate or low-quality spam reports.

- Document any retracted finding in an appendix with the original signal, the disproving evidence and why it looked like a bug, because a clean report with a retraction appendix is more trustworthy than one where findings silently disappear.

## Attribution

- The method in this skill is distilled from Claude-BugHunter by Sachin Sharma, licensed CC BY 4.0, at https://github.com/elementalsouls/Claude-BugHunter — clone it for the full bundle and the per-class skills, which carry the full detection patterns, payloads and chain templates.

- The report structure, pre-writing checks, acceptance tips and common mistakes above follow the guide by @Airdropfinds, "Cara bikin laporan Bug Bounty yang bener", 18 Nov 2026, https://x.com/Airdropfinds/status/2122985446989086967.
