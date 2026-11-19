# Motion Design and Programmatic Video

## What this is

- A pipeline for making motion design and short videos with code, not with a video editor. Source: a curated list of 20 repos and skills by @okapi_fukugyo (17 Nov 2026, https://x.com/okapi_fukugyo/status/2122626196949311747). Every repo below was verified to exist on 18 Nov 2026, either by resolving its link or through the GitHub API.

- The workflow is skill, then scene, then motion, then sound, then export. Pick the job first, then the engine that fits it, then build the scene, animate it, add sound and subtitles, and export with FFmpeg.

## When to use it

- Short promo videos for X posts, project trailers, and the pink shark brand.

- Explainer videos for a bounty that asks for one, and motion for a game entry (trailers, animated screenshots, menu and HUD motion).

- Product reveals and assembly diagrams that need to show how something is built.

## The pipeline

- Principles first. Read the motion-design skill before animating anything. Timing, easing and Disney's 12 principles decide whether motion feels good. The skill is https://github.com/LottieFiles/motion-design-skill.

- Build the scene. For 3D use Three.js (https://github.com/mrdoob/three.js). For a React scene use Remotion (https://github.com/remotion-dev/remotion) or react-three-fiber with react-three-rapier for real physics (https://github.com/pmndrs/react-three-rapier) and react-postprocessing for cinematic light, blur and bokeh (https://github.com/pmndrs/react-postprocessing). For particles use three.quarks (https://github.com/Alchemist0823/three.quarks).

- Animate it. For web animation use Motion (https://github.com/motiondivision/motion) for springs and transitions, or GSAP (https://github.com/greensock/GSAP) for timelines. GSAP is free. For math and explainer animation use Manim (https://github.com/ManimCommunity/manim). For light vector animation use Lottie (https://github.com/airbnb/lottie-web).

- Tune it live. Use Tweakpane (https://github.com/cocopon/tweakpane) to adjust parameters directly while the scene runs instead of editing code and re-rendering.

- Add sound. Find free sound effects, ambient sound and music through the Openverse API (https://api.openverse.org) with no API key. Sync motion to a song's beat with librosa (https://github.com/librosa/librosa).

- Add subtitles. Use WhisperX (https://github.com/m-bain/whisperX) for automatic subtitle timing with word level timestamps.

- Export with FFmpeg (https://github.com/FFmpeg/FFmpeg) for conversion, trimming, compression and the final file.

## Agent skills in the list

- Remotion's official skills (https://github.com/remotion-dev/skills) teach an agent how to make videos with Remotion. Read its SKILL.md before building a video with it.

- The hairline skill (https://hairline.lucasmarkes.com/skills) turns an idea or an SVG into touchable moving sketch lines.

- The anatomy skill (https://skills.wheresryan.sh/anatomy) turns a machine or a mechanism into a 3D illustration.

- The anatomy-reveal skill (https://typingmind.com/skills/annnguyentt-anatomy-reveal) builds product assembly diagrams and climax videos.

- Blender (https://github.com/blender/blender) covers 3D rigging and character animation. It is a full 3D suite, not a library.

## Pick the engine by the job

- A short promo or social video: Remotion plus GSAP or Motion, sound from Openverse, subtitles from WhisperX, export with FFmpeg.

- A product reveal: the anatomy and anatomy-reveal skills, Three.js for the scene, Tweakpane to tune the reveal.

- A game trailer or animated menu: Three.js plus react-three-rapier and react-postprocessing, GSAP for the timeline, FFmpeg for the export.

- An explainer with maths or diagrams: Manim, then FFmpeg.

- A light looping animation on a page: Lottie.

## Environment notes

- FFmpeg, Remotion, GSAP, Motion, Lottie, librosa and Manim run fine on modest hardware. Blender and WhisperX are heavy; run them on a bigger machine or skip them.

- Remotion renders with a headless browser. Use a system Chrome/Chromium for rendering.

## Safety

- Check every repo and tool before installing it. Do not install or add anything suspicious or dangerous. Read an individual skill's SKILL.md first and never run an install script blindly. The big official repos above are well known and high star. The small individual skill pages are community work and need a read before use.

## make.fun entries

- These tools are libraries and skills, not entry code. When a bounty entry needs video or motion, author the entry code in session as usual. Vendor a library under `game/vendor/` or as a `*.min.js` file where the kit allows it, because vendored files are not counted as the agent's source.

## Related skills

- [Bug Hunting and Security Review](../bug-hunting/SKILL.md) for vetting a repo before installing it.
