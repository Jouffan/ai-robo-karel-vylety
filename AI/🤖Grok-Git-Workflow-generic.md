# 🚀 Grok Git Workflow & Safety Rules (generic)

Portable template for any GitHub project that Grok edits through the GitHub
connector, especially repos that use **emoji / emoticon characters in
filenames**. Copy this file into the target repo and fill in the boxed
project values. Do not leave the placeholders in a live instruction file.

```
PROJECT VALUES (fill these)
  owner:              <github-owner>
  repo:               <repo-name>
  default branch:     main
  commit prefix:      [🚀Grok]
  branch prefix:      ai/grok-
  working copy roots: chat drafts, sandbox artifacts, project memory
                      (none of these are canon)
```

This file overrides general chat instructions for branch / push / verify /
merge / emoji paths in **this** repository.

Canon lives only on GitHub. Sandbox folders, chat drafts, and memory are
working copies until a verified push lands.

There is no local clone of the repo in the Grok sandbox. Do not run `git`
against it. Use GitHub connector tools only.

## Core Principles

- Each chat: decide together — work on the default branch, or open a named
  working branch.
- Branch names must describe the task:
  `ai/grok-[task]-[YYYYMMDD]` (ASCII only — see Emoji section).
- Never report a successful push until a re-fetch matches the intended
  bytes **and** the intended path.
- Merge to the default branch only when the user explicitly says to merge.
- Do not create, rename, or delete files whose names contain emoji unless
  the path was copied from a live directory listing (or the user pasted it).
- Do not use GitHub Copilot agent / `create_pull_request_with_copilot`
  unless the user explicitly asks for it on this repo.

Add project-specific bans under **Project addenda** at the bottom. Keep
them out of the generic body.

## Tools (current Grok GitHub connector)

| Job | Tool | Notes |
|---|---|---|
| Read file or list a folder | `github___get_file_contents` | Always pass `ref` (`refs/heads/main` or the working branch). First text result includes blob SHA. |
| Discover paths | `github___get_repository_tree` / `github___search_code` | Do not load whole trees into context. |
| Create branch | `github___create_branch` | `from_branch` = default branch unless told otherwise. |
| Update one existing file | `github___create_or_update_file` | **Must** send current blob `sha` from a fresh get. Content is raw text, not base64. |
| Commit several files together | `github___push_files` | Use when two or more files must stay in sync. |
| Delete | `github___delete_file` | Only with explicit user instruction. |
| PR / merge | `github___create_pull_request` then `github___merge_pull_request` | `merge_method: "merge"`. Pass `expectedHeadSha`. |
| History | `github___list_commits` / `github___list_branches` | Session start: confirm tip SHA before editing. |

Tool names may change. If a name is missing, search connected tools and
use the equivalent. The **rules** (SHA on update, re-fetch, copy paths)
do not change.

## Session start (git)

1. Confirm `owner` / `repo` / default branch with the user if this chat
   has not already locked them.
2. `list_commits` on the agreed ref.
3. Record tip SHA.
4. Read files with `ref` set. Never edit from a truncated body.
5. Resolve emoji paths by listing the parent folder and copying `path` /
   `name` verbatim (see Emoji section).
6. If the user did not name a branch, ask before creating one.

## When to use a branch vs the default branch

- **Default branch (`main`)**: small locked-scope polish the user told you
  to apply now (typo, one agreed sentence, instruction tweak already
  reviewed).
- **Working branch**: new long files, multi-file locks, anything that
  could truncate or collide with another session.

Do not leave exploratory `ai/grok-session-…` branches unless the work is
genuinely unscoped.

```
ai/grok-fix-readme-links-20260912
ai/grok-add-docs-index-20260912
```

## Emoji in Git (mandatory)

Emoji in a filename is identity, not decoration. A near-miss prefix
creates a **second file** or an empty “emoji folder.” Treat every path as
a raw Unicode string.

Two different jobs — do not mix them:

| Job | Where | Git risk |
|---|---|---|
| Filename prefix / folder name | `path`, `name` | High — wrong bytes = ghost file |
| Commit / PR label | subject line | Low if the agreed prefix is copied exactly |
| Marks **inside** file text | file body | None for Git. Do not strip or rewrite them during a push. |

If the project also uses emoji as in-document editor marks, those rules
belong in a separate conventions file. This workflow only governs Git
paths and Git metadata.

### Copy. Do not reconstruct.

1. Resolve a file by listing its parent folder (`get_file_contents` on
   the directory, or `get_repository_tree` with a path filter).
2. Copy the `path` and `name` fields **verbatim** into the next tool call.
3. Never type an emoji prefix from memory if a listing is available.
4. The ASCII tail is the disambiguator:
   `Quarterly-Report.md` is unique; `📄` is not.

If the returned name is mojibake, a replacement character (`�`), a
Greek/Latin lookalike, a stripped variant selector (`♀` instead of `♀️`),
or a `%01…` / `%F0%9F…` stub: **stop**. Do not push. List the parent
again and match on the ASCII tail.

### Tool-argument rules

- Pass the path as real Unicode in `path` / `files[].path`.
  Do **not** percent-encode (`%F0%9F%9A%80…`). The connector encodes.
  Encoded input can create a second file whose name is the `%xx` string.
- Do not normalize lookalikes. Common traps:

  ```
  🚀 ≠ 🤖 ≠ 🐣 ≠ 🌙
  📄 ≠ 📃 ≠ 📝 ≠ 📑
  📁 ≠ 📂
  ✔️ ≠ ✅ ≠ ✓
  ❤️ ≠ ❤  (variant selector)
  ♀️ ≠ ♀
  ♂️ ≠ ♂
  ⚠️ ≠ ⚠
  ```

  Same visible idea, different code points, different Git objects.
- Never create a file or folder whose name is **only** an emoji.
- Never “fix” a prefix on write. Update the existing path or ask.
- Do not NFC/NFD-normalize a path “to be safe.” Use the bytes GitHub
  already stored.

### Where emoji is allowed

| Place | Rule |
|---|---|
| Existing filename or folder | Reuse the listed string. Do not invent a new prefix. |
| New file in an existing family | Copy the prefix from a **sibling in that folder**. If the folder has no siblings yet, ask the user which prefix the family uses. |
| New family of files | Ask. Do not start a new emoji prefix scheme unprompted. |
| Branch name | **ASCII only.** |
| Commit subject | Agreed prefix only (default `[🚀Grok]`). No extra emoji in the subject. |
| PR title | ASCII preferred. The commit prefix is allowed if it matches the commits. |
| File body | Emoji in content is safe. Do not strip it during a Git write. |

### After every write to an emoji path

Re-fetch and check **three** things, not just the text:

1. `path` / `name` equal the intended Unicode (not a lookalike).
2. Parent directory still has **one** file with that ASCII tail.
3. Size is plausible. A 200-byte file where a 30 KB file just was means
   you hit a different path or truncated.

If a second file appeared next to the real one, delete only the ghost,
and only after showing the user both paths.

### Do not “clean up” prefixes

Do not rename `📄Report.md` → `Report.md` to avoid encoding pain. If the
project chose emoji prefixes, that scheme is canon until the user says
to migrate. Encoding pain is solved by copy-from-listing, not by
stripping marks.

### Optional prefix-family table

Fill this in per repo so a new session does not guess:

| Folder / family | Prefix | Example ASCII tail |
|---|---|---|
| *(example)* docs | 📄 | `Overview.md` |
| *(example)* people | ♀️ / ♂️ | `Ada.md` |
| *(example)* places | 🚩 | `Studio.md` |
| *(example)* plans | 💡 | `Roadmap.md` |
| *(example)* Grok instructions | 🚀 | `BOOTLOADER.md` |
| *(example)* shared instructions | 🤖 | `Style.md` |

Delete the example rows when you adopt the file.

## Push protocol

1. Read the live file on the target branch. Keep its blob SHA.
2. Build the **full** replacement file. Never push a slice as the whole file.
3. Choose:
   - one file, SHA in hand → `create_or_update_file`
   - two or more files that must move together → `push_files`
4. Commit subject **must** start with the agreed prefix. Remainder ASCII.
5. Immediately `get_file_contents` on the same path + `ref`.
   Confirm: intended text is present, length is plausible, new SHA ≠ old
   SHA (unless the write was a no-op), and the returned `path` is the
   same Unicode.
6. Report success only after that check. Include the new commit SHA.

If the first verify mismatches, stop and re-read. A second get is a
fallback, not a ritual.

### Hard bans

- Do not push a truncated read back onto GitHub.
- Do not split one file across sequential “part 1 / part 2” overwrites.
  Full-file replace only. Partial overwrites have destroyed long files.
- Do not invent a path that “looks like” the real one.
- Do not percent-encode paths in connector arguments.

### If verify fails more than twice

Stop pushing. Tell the user what came back (SHA, size, first/last lines,
returned path). Wait.

## Merge to the default branch

Only after an explicit “merge it” (or equivalent).

1. Confirm the working branch is verified.
2. `list_pull_requests` so a duplicate PR is not opened.
3. `create_pull_request` (`head` = working branch, `base` = default).
4. `merge_pull_request` with `merge_method: "merge"` and `expectedHeadSha`.
5. Re-fetch the file(s) from the default branch and confirm path + bytes.
6. Mention leftover working branches; delete only if the user asks.

The full review dance can be skipped when the user says so. Copilot
review is optional and never blocking.

## Companion files in the same commit set

When a change makes an index, manifest, README pointer, or status file
wrong, update those files in the **same** push. Do not “refresh later”
as a substitute for the commit that changes canon.

List the companion files for this repo here:

- *(example)* `README.md` if it links the touched path
- *(example)* a FILE-INDEX / manifest if the project has one

## Problems this prevents

| Problem | Guard |
|---|---|
| Hallucinated / silent failed push | Re-fetch before reporting |
| Truncated file overwrite | Full-file replace only; size check on verify |
| SHA mismatch on update | Fresh blob SHA from get |
| Cross-session collision | Named branch when the edit is large |
| Ghost emoji file / broken emoji folder | Copy path from listing; verify `name` after write |
| Percent-encoded second path | Never send `%xx` in `path` |
| Lookalike prefix (`♀` vs `♀️`, `📄` vs `📃`) | Compare against listed `name`, not against memory |
| Stale index after a lock | Companions ride with the change |

## Quick reference

| Action | Allowed | Condition |
|---|---|---|
| Push to default branch | Yes | User said to, or chat agreed this is a small polish |
| Open `ai/grok-…` branch | Yes | Agreed in chat |
| Create + merge PR | Yes | User said merge |
| Merge without being asked | No | |
| Skip post-push verify | No | |
| Chunk-overwrite a long file | No | |
| Invent / encode / “fix” an emoji path | No | |
| Rename to strip emoji prefixes | No | Unless the user asked for a migration |
| Copilot-agent PR | Only if the user asked | |

## How to adopt in a new project

1. Copy this file into the repo (pick a path; keep the `🚀` prefix only
   if that family already exists there).
2. Fill **PROJECT VALUES** and the prefix-family table.
3. Add **Project addenda** (lock rules, private folders, second-AI
   isolation, placeholder policy).
4. Point the project’s main instructions at this file with the **exact**
   listed path — do not cite a filename that is not in the tree.
5. First session: list the instruction folder and confirm one file with
   this ASCII tail.

## Project addenda

_Leave empty in the template. Per-repo rules go here so the generic
body stays reusable._
