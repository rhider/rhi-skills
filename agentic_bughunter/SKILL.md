# Agentic Bug Hunter CLI and Web3 Audit

## When to use this skill

- Use this skill when the user asks to run a full hunt from the terminal, audit a smart contract or token, or work a lead board of findings.

- Use it for defensive review of the user's own code and contracts and for authorized bug bounty targets only.

- Never use it against a target the user does not own and has no written authorization to assess.

- The method and the seven question gate are shared with the `bug_hunting` skill, because both bundles come from the same author lineage, so use `bug_hunting` for the 83 per-class webapp patterns and use this skill for the CLI runner, the web3 audit and the lead board.

## Run the standalone CLI

- The `bughunter` command runs recon, hunt, validate and report from the terminal without a Claude Code subscription. Install it from the upstream repo (see Attribution) and run `bughunter setup` to pick a provider.

- Free provider choices are Ollama running locally with no key, Groq on its free tier with an API key, or OpenRouter's `:free` models with a free API key. Never paste a key in chat and never commit one to a file.

- The setup wizard prompts for the API key even when the environment already holds it, so run setup with a blank line on stdin or it waits forever. The config is saved before the connection test, and the test can print no reply for a reasoning model while the setup still succeeds.

- After install, the commands are `bughunter setup` to pick the provider, `bughunter recon target.com` to map the surface, `bughunter hunt target.com` to test for vulnerabilities, `bughunter validate "finding"` to run the seven question gate, `bughunter report` to write the submission and `bughunter chat` for an interactive hunting shell.

- The CLI reuses recon and scanning tools already installed on the machine, such as subfinder and nuclei, and skips any tool that is missing instead of failing.

- Output lands in `~/.bughunter/` unless the user sets `BUGHUNTER_HOME` to another path.

## Available connectors

- [OpenRouter](https://openrouter.ai/) supplies free models the CLI can run on.

## Work the lead board

- After recon, ingest every lead into the board before you hunt so no finding is forgotten.

- Work one lead at a time and update its status when you start it, kill it or report it.

- Route each lead to its matching skill in plain language, such as a GraphQL endpoint going to the GraphQL audit skill.

- Surface stale high priority leads unprompted when you start a session.

- The board lives in the bundle's `bughunter/memory/` directory and the tool that manages it is `bughunter/tools/lead_board.py`.

## Audit smart contracts and tokens

- Use the web3 audit when the user gives you a contract or a token to review, because it covers ten smart contract bug classes plus a Foundry proof of concept template.

- Check accounting desync, access control, incomplete code paths, off by one errors, oracle manipulation, ERC4626 share inflation, reentrancy, flash loan attacks, signature replay and proxy upgrade issues.

- Use the token scan when the user gives you a token contract, because it checks mint authority, liquidity pool locks, honeypot behaviour and bonding curve abuse.

- Read the bundle's `skills/web3-audit/SKILL.md` before an audit and `skills/meme-coin-audit/SKILL.md` before a token scan.

- Report a contract finding with the exact vulnerable function, the attacker steps and the funds at risk, because a vague contract finding is not payable.

## Use the extra skills in this bundle

- Read the bundle's `skills/mcp-server-audit/SKILL.md` when the target is an MCP server, because it covers tool poisoning, parameter to sink injection, missing approval gates and secret leaks.

- Read the bundle's `skills/cicd-security/SKILL.md` when the target is a CI pipeline, because it covers GitHub Actions injection, secret exfiltration and self-hosted runner poisoning.

- Read the bundle's `skills/graphql-audit/SKILL.md` for a GraphQL target, because it covers introspection, field suggestion abuse, batching denial of service and IDOR through aliasing.

- Read the bundle's `skills/cloud-pentest/SKILL.md` after you hold cloud credentials, because it covers IAM enumeration, privilege escalation and metadata credential abuse.

- Read the bundle's `skills/llm-redteam/SKILL.md` when the target is an LLM endpoint, because it covers prompt injection, jailbreak and data exfiltration.

- Treat the credential attack skill as opt-in only and stop before any password spray, because spraying needs a separate human go ahead every time.

## Attribution

- The method and CLI in this skill come from Agentic-Bug-Hunter by AwareXone, licensed MIT, at https://github.com/awarexone/Agentic-Bug-Hunter — clone it for the full bundle, the CLI source and the extra audit skills.
