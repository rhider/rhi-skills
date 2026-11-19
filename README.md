# rhi-skills 🦈

6 agent skills yang dipakai **Rhi** — asisten AI-nya [@RhiderShark](https://x.com/RhiderShark) — sehari-hari buat ikut bounty, audit keamanan, dan bikin video. Dibagikan apa adanya, gratis, biar teman-teman bisa pakai juga.

> Skill di sini adalah playbook (file `SKILL.md`) buat AI coding agent: dibaca agent sebelum kerja, bukan kode yang dieksekusi. Cara pakai: copy folder skill yang kamu butuh ke direktori skills agent kamu (mis. `~/.claude/skills/` buat Claude Code, atau folder custom-skills di agent kamu), lalu minta agent membaca `SKILL.md`-nya sebelum mulai kerja.

## Isinya

| Skill | Buat apa | Sumber |
|---|---|---|
| [makefun_bounty_entries](makefun_bounty_entries/SKILL.md) | Masuk bounty [make.fun](https://make.fun/r/q4c7yqs4): baca brief + leaderboard dulu, build sesuai kit, kit-check, submit, verifikasi status server, posting komentar entry | Playbook Rhi, hasil 25 entry make.fun |
| [aiprove_bounty_entries](aiprove_bounty_entries/SKILL.md) | Masuk bounty AIProve (beta): cek live apakah bounty benar-benar bisa dimasuki gratis, auth keypair, submit + verifikasi `provenance_ok` | Playbook Rhi, hasil 13 submission AIProve |
| [bug-hunting](bug-hunting/SKILL.md) | Cari & validasi bug keamanan di kode sendiri / target resmi: workflow 5 fase, 7-question gate, laporan impact-first | Distilled dari [Claude-BugHunter](https://github.com/elementalsouls/Claude-BugHunter) (Sachin Sharma, CC BY 4.0) |
| [agentic_bughunter](agentic_bughunter/SKILL.md) | Jalankan `bughunter` CLI dari recon sampai report, kerja lead board, audit smart contract & token | Dari [Agentic-Bug-Hunter](https://github.com/awarexone/Agentic-Bug-Hunter) (AwareXone, MIT) |
| [anthropic_skills](anthropic_skills/SKILL.md) | Katalog + router skill resmi Anthropic: docx, pdf, pptx, xlsx, frontend-design, web-artifacts-builder, webapp-testing, generative art, MCP builder, skill-creator | [Anthropic skills](https://github.com/anthropics/skills) (Apache 2.0) — file ini hanya katalog, clone repo upstream buat isi lengkapnya |
| [motion_video](motion_video/SKILL.md) | Bikin motion design & video pendek pakai kode: Remotion, Three.js, GSAP, Motion, Manim, Lottie, FFmpeg, WhisperX, librosa | Kurasi dari list [@okapi_fukugyo](https://x.com/okapi_fukugyo/status/2122626196949311747) |

## Aturan main

- **Bug hunting hanya buat kode sendiri atau target yang kamu punya izin tertulis buat diuji.** Jangan dipakai buat nembak target orang lain tanpa izin.
- **Cek dulu sebelum install.** Setiap skill yang nunjuk ke repo/tools pihak ketiga — baca repo-nya dulu sebelum install atau jalanin script-nya.
- **Jangan masukin secret ke repo.** Skill-skill di sini tidak berisi API key, wallet, atau kredensial apa pun. Kalau kamu adaptasi buat setup sendiri, simpan kredensial di luar repo.
- Skill `makefun` / `aiprove` ditulis dari pengalaman nyata ikut bounty gratis — hadiah dan aturan bisa berubah, selalu baca brief live sebelum build.

## Kredit

- Claude-BugHunter — Sachin Sharma ([@elementalsouls](https://github.com/elementalsouls)), CC BY 4.0
- Agentic-Bug-Hunter — AwareXone, MIT
- Anthropic official skills — Apache 2.0
- Motion video list — [@okapi_fukugyo](https://x.com/okapi_fukugyo)
- Panduan nulis laporan bug bounty — [@Airdropfinds](https://x.com/Airdropfinds/status/2122985446989086967)

## Lisensi

MIT — lihat [LICENSE](LICENSE). Atribusi di atas tetap berlaku buat karya upstream-nya.
