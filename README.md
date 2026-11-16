# My Pi developer setup

My personal [Pi](https://pi.dev/) extension selection and settings for software development. This is a reference for developers who already know Pi and want to complement their own setup, not a turnkey distribution or a set of agent instructions.

The repository lives directly in my `~/.pi`. [agent/settings.json](agent/settings.json) is my active configuration, with the installation-specific `deviceId` omitted from commits. Models and preferences are intentionally retained so you can see the actual choices and adapt them.

**Environment:** used on Linux with Pi **1.5.2**. Pi and package versions are not pinned by this repository. Releases capture configuration choices, not reproducible dependency snapshots. I update the repository after substantial changes to my setup; there is no support or compatibility guarantee.

## Extension selection

The `packages` array in [settings.json](agent/settings.json) is authoritative. Pick the packages you need rather than treating the whole list as mandatory.

| Package | Why it is in this setup |
| --- | --- |
| [pi-web-access](https://www.npmjs.com/package/pi-web-access) | Web research and content retrieval. |
| [pi-smart-fetch](https://www.npmjs.com/package/pi-smart-fetch) | Browser-fingerprinted fetching and readable page extraction. |
| [pi-tool-display](https://www.npmjs.com/package/pi-tool-display) | More compact tool output and diff display. |
| [pi-session-search](https://www.npmjs.com/package/@kaiserlich-dev/pi-session-search) | Search previous Pi sessions. |
| [pi-session-analyzer](https://github.com/catlain/pi-session-analyzer) | Inspect session history, branches and activity. |
| [pi-codex-usage](https://www.npmjs.com/package/@calesennett/pi-codex-usage) | Provider usage visibility. |
| [pi-save-output](https://www.npmjs.com/package/@nonplanarslicer/pi-save-output) | Save assistant output. |
| [pi-subagents](https://github.com/nicobailon/pi-subagents) | Delegate bounded work and run multi-agent workflows. |
| [pi-intercom](https://github.com/nicobailon/pi-intercom) | Communicate between Pi sessions. |
| [pi-runtime-monitor](https://github.com/ZEDIUM-Off/pi-runtime-monitor) | Observe session processes, CPU and memory. |
| [pi-lsp-extension](https://github.com/samfoy/pi-lsp-extension) | Code diagnostics and language-server navigation. |
| [pi-context-view](https://www.npmjs.com/package/pi-context-view) | Inspect context. |
| [accordion](https://www.npmjs.com/package/@a-fig/accordion) | Fold and recall long conversation context. |
| [pi-claude-directsdk](https://github.com/joaomj/pi-claude-directsdk) | Claude provider integration through the Claude Code executable. |
| [pi-auto-title](https://github.com/ItsNerisma/pi-auto-title) | Generate session titles automatically. |
| [pi-codex-image-gen](https://www.npmjs.com/package/pi-codex-image-gen) | Generate and edit images through the Codex backend. |
| [pi-tasks](https://www.npmjs.com/package/pi-tasks) | Track task plans, acceptance criteria and verification evidence. |
| [pi-split-view](https://www.npmjs.com/package/pi-split-view) | Show thinking, tool activity and files in separate TUI panels. |

Codemode is enabled with `defaultTools: ["+codemode"]`. It is built into the Pi version used here, not another package to install.

Some packages overlap intentionally: session search and analysis, web access and fetching, or different coordination workflows. Keep only what fits your use. Consult each package's documentation for its dependencies, authentication, capabilities and security implications. LSP requires suitable language servers; Claude Direct SDK requires its own supported Claude Code setup.

## Reuse in an existing setup

1. Review the package sources and your existing settings; keep a private backup before editing.
2. Install selected entries with `pi install <source>`, using their exact source strings from this repository. For example:

   ```sh
   pi install git:https://github.com/nicobailon/pi-subagents
   ```

3. Merge only the preferences you want into your own `~/.pi/agent/settings.json`.
4. Authenticate with your own providers and select models available to you.
5. Start a fresh session, inspect loading errors, and test the tools you selected on a non-sensitive project.

**Do not overwrite an existing `~/.pi` with this repository or recursively copy its `.git` directory into another installation.** You do not need to clone this repository to reuse its extension list.

### Settings to adapt

- **Models:** `defaultProvider`, `defaultModel` and `enabledModels` reflect my access and preferences. They do not grant access or guarantee availability. Replace them as needed; private model catalogs and credentials are not included.
- **Package manager:** my `npmCommand` uses `pnpm` with `--config.dangerously-allow-all-builds=true`. This permits dependency build scripts. It is a trust decision, not a requirement: remove the override to use Pi's default package manager, or choose your own policy.
- **Skills:** the `skills` array is empty. Add your own resource filters if needed.
- **UI and images:** the system theme, fullscreen TUI, quiet startup and disabled image resizing are personal preferences. Keeping original image sizes can increase payloads.
- **Changelog markers:** `lastChangelogVersion` and `extensionChangelogVersions` record previously seen versions; they are not dependency pins. You can omit them when adapting the file.
- **Device identity:** the published file omits `deviceId`. Let Pi generate your own installation identifier when needed; do not copy one from another installation.

## Skill ownership

I use `~/.agents/skills/` as my main shared skill directory. The Pi-managed locations under `~/.pi` are reserved for skills supplied by installed Pi extensions/packages. Those skills stay with their owning package so that package updates also update the skills.

The current settings have no explicit skill exclusions. This repository does not distribute my shared skills or agent instructions.

## Updates

Commands verified against Pi 1.5.2's installed help and documentation:

```sh
pi update                        # Update Pi itself
pi update --extensions           # Update installed packages
pi update --extension git:https://github.com/nicobailon/pi-subagents
pi update --all                  # Update Pi and installed packages
```

`--extension` takes a package source; `--extensions` updates all packages. Package-owned skills follow their package update. A package-manager-managed Pi installation may need its own update mechanism.

There are no version or commit pins in the package declarations. Upstream changes can introduce incompatibilities. Review changelogs and verify your workflows after updates. Removing a pin from settings does not itself update an installed package.

## Publication boundary

Only these files are allowlisted:

- `agent/settings.json` — public settings, excluding `deviceId` in the committed version;
- `README.md`, `LICENSE`;
- `.gitignore` and `.gitleaks.toml`.

Credentials, model configuration, agent instructions, sessions, histories, skills, caches and installed packages are not distributed. If a credential is accidentally published, revoke or rotate it immediately; deleting it in a later commit does not remove it from Git history.

The live settings retain my device ID while the committed version omits it. Consequently, `git status` normally reports settings as modified after a publication commit. **A later `git add` or `git commit -a` can reintroduce the identifier.** Review the indexed content, not just the filenames, before every commit. Ignore rules cannot protect individual JSON fields or files already tracked by Git.

## Verification and limits

This refresh was prepared from a Linux installation running Pi 1.5.2. Preparation checks cover JSON validity, unpinned package declarations, the publication allowlist, exclusion of device identity from the commit, and the documented update command syntax.

This is not a clean-install certification or an end-to-end test of every extension. Preparation did not update installed packages, exercise provider authentication or qualify macOS/Windows. A future installation may resolve newer dependencies than the ones used locally.

Compared with the previous publication, this refresh removes Pi Studio, Pi Messenger and Ponytail. It adds Split View, Tasks, Auto Title and Codex Image Gen to the published selection and reflects the current fullscreen TUI preference. No private workflow instructions are included.

## Maintenance and license

Shared as-is, updated when my setup changes substantially. Use upstream package issue trackers for their bugs; each dependency retains its own license and terms. This repository's configuration and documentation are provided under the [MIT license](LICENSE).
