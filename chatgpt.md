# ChatGPT / Codex capabilities

Verified: 2026-10-18 (America/New_York). Repository: [Mrice90/InfiniteJutsu](https://github.com/Mrice90/InfiniteJutsu).

This is a snapshot of the Codex desktop session used to prepare this document, not a promise that every future ChatGPT chat has the same access. Recheck the active tools, skills, permissions, and project instructions before starting work.

## What I can help with

- Inspect a codebase, explain behavior, implement changes, debug failures, review diffs, run available tests, and prepare documentation and pull requests.
- Research questions using connected sources and the web, distinguish evidence from assumptions, and produce sourced summaries.
- Create and revise writing, images, documents, spreadsheets, presentations, PDFs, and websites using the relevant available tools and skills.
- Coordinate project work through repository evidence, ownership records, and authorized chat or automation tooling.

## Tools and availability

“Exposed” means the session offers the tool, not that its service authentication or every operation was tested.

| Capability | Available surface | Practical boundary / verification |
| --- | --- | --- |
| Local development | PowerShell command execution, file search, patch editing, process input, image inspection | Reads and searches worked. Writes are limited to permitted workspace/temp locations; network and protected paths can require approval. Installed runtimes must be checked per project. |
| GitHub | Connected repository/file/commit/branch/PR tools; issue, review, and workflow tools | Repository access and documentation writes verified for this repository. This task leaves changes in a PR; no merge. |
| Web research | Search, page retrieval, PDF screenshots, and specialist lookup tools | Search and official documentation retrieval verified. Cite evidence; access to a URL is not access to private content. |
| Browser interaction | CUA browser/tab inspection and interaction | Exposed; not exercised for this task. Native desktop-app control is disabled in this session, despite the installed computer-use skill. |
| Images | Built-in image generation/editing and local image viewing | Exposed; generation not exercised. Follow the image skill and use the supported image tool. |
| Codex app management | Read/list/manage chats, projects, worktrees, sidebar items, artifacts, and automations | Chat listing verified. New chats and recurring work require the user's request; nothing runs indefinitely merely because it was discussed. |
| Team assistance | Sub-agent tools and chat coordination | Available subject to session instructions; this session permits sub-agents only when explicitly requested or required by applicable instructions. |
| Structured artifacts | Documents, presentations, spreadsheets, PDF, visualization, template skills; workspace dependency loader; connected document sessions | Skill/runtime availability does not establish an active Word/Excel document session or guarantee every export format. |
| Connected services | GitHub, Google Drive/Docs/Sheets/Slides, Gmail, Google Calendar, Slack, Notion, ElevenLabs, Canva, Sites, OpenArt, Etsy, Kahoot, Quizlet, and Work Pets tool families | Exposed in the session catalog; except GitHub, account access and operations were not tested for this documentation task. Use only the authorized data and actions. |
| Plugin administration | Plugin discovery, connection, permissions, and management tools | Exposed. A recommended plugin is not an installed or authenticated capability. |
| Unity | Installed Unity skills for CLI/editor work, UI, audio, rendering, sprites/tilemaps, localization, packages, multiplayer and services | No direct Unity connector tools appeared in this session's callable-tool catalog. CLI/editor work needs a usable local installation, project, connection, and applicable instructions. |
| Meshy | Installed 3D generation and printing skills | No direct Meshy connector tools appeared in this session's callable-tool catalog. Do not claim generation or account access without establishing a supported execution route. |
| ElevenLabs | Exposed voice-agent and media tools plus agent, speech, music, sound, transcription and dubbing skills | Service/credit/voice permissions and job outcomes must be verified per request; no media was generated in this task. |

Other specialized exposed tools include code-review checks, safety settings, and helpline lookup. Their presence is not authorization to access or change unrelated account data.

## Skills versus tools

A skill is a reusable workflow described by a `SKILL.md` file and optional supporting resources. Tools perform actions; skills guide their use. See [OpenAI's skill documentation](https://developers.openai.com/plugins/concepts/skills).

The installed catalog includes system skills (OpenAI Docs, image generation, skill creation/installation) and vendor/plugin workflows for Unity, ElevenLabs, Meshy, Drive, Notion, Sites, documents, presentations, spreadsheets, PDFs, visualization, computer use, templates, and Work Pets. These are not skills I authored for Matt's projects.

See the [project skill inventory](docs/project-skill-inventory.md) for verified files, purposes, project associations, provenance, and search limitations.

## Working boundaries

- Read applicable `AGENTS.md` and project coordination records; preserve others' changes and reserved resources.
- Use `chatgpt.md` for this capability reference. Do not edit Claude's file as part of this request.
- Keep read-only synced `sources/` untouched. Work in an authorized checkout or via the connected repository tools.
- Report what was actually run and verified. A skill listing, intended action, or generated artifact is not evidence of a successful build, deployment, purchase, or service operation.
- Send messages to other people only when explicitly authorized. Respect project restrictions on spending, protected branches, and external changes.
- Future sessions must refresh this snapshot rather than treating it as a permanent access grant.
