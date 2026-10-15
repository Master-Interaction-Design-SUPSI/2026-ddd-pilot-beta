# Group repository: student guide

Your group's public repository. Your group edits text and media here. The [course repository](https://github.com/Master-Interaction-Design-SUPSI/2026-ddd-making-sense-of-data) imports them and publishes the course website.

**WARNING**: Everything here is public. Upload only material cleared for publication.

## 1. Prerequisites

- GitHub account and browser. Nothing to install.
- One repository per group. One member opens the [group template](https://github.com/Master-Interaction-Design-SUPSI/2026-ddd-pilot-beta) → **Use this template → Create a new repository**. Owner: your account. Visibility: **Public**. Then **Settings → Collaborators → Add people** for each teammate. Send the repository link to the course team.
- From the course team: group identifier (slug), website link.
- Publication starts when the course team confirms setup.
- The supplied text, visual, `media.csv` and `media/example-*` files are demonstrations with invented numbers. Replace them. Delete a file only after removing its reference from `text.md`.

## 2. Files

| Path | Role | Rule |
| --- | --- | --- |
| `text.md` | Text | Required. Front matter: title, authors. |
| `media.csv` | Media table | Required. First line `name,source,file`; one row per media file used in `text.md`. |
| `visual.svg` | Main visual | Required unless the course team exempts your group. 1920 × 1080 SVG. |
| `media/…` | Extra images, audio, video | Optional. Listed in `media.csv`, named in `text.md`. |

Everything else (this README, design sources, HTML, scripts) is ignored and never published.

## 3. Edit text

1. Sign in. Open your group's repository. Accept the invitation first if another student owns it. Branch menu: **main**.
2. Open `text.md`; click the pencil icon.
3. Replace title, authors and paragraphs. Keep both `---` lines:

   ```text
   ---
   title: Your project title
   authors: Your group members
   ---

   What question did you investigate?

   Explain what you found and how you worked with the data.
   ```

4. **Commit changes** → **Commit directly to the main branch** → confirm.

GitHub offers only a fork or a proposed change: wrong repository, or invitation not accepted. Ask the course team to check your access. Reference: [GitHub editing guide](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files).

## 4. Upload main visual

1. Export the whole 1920 × 1080 px frame as SVG, named `visual.svg`. Renaming a PNG or JPG to `.svg` converts nothing.
2. Repository root → **Add file → Upload files** → `visual.svg` → commit to **main**. The same name replaces the previous file.
3. Required attribute: `viewBox="0 0 1920 1080"`. Width and height, if present: 1920 and 1080 px.
4. One main visual only. Delete any `visual.png` or `visual.jpg`: **… → Delete file** → commit to **main**.

`text.md` and `visual.svg` stay at the root. No group folder.

## 5. Add media

1. Open `media/` (or the root) → **Add file → Upload files** → commit to **main**.
2. Add a row to `media.csv` at the root: the name you write in the text, the link to the original source, the file's exact path. Commit.

   ```text
   name,source,file
   interview,https://archive.org/details/example-interview,media/interview.mp3
   lithium mine,https://example.org/photo-of-the-mine,media/mine.jpg
   ```

3. Write the name in double brackets in `text.md`: `[[interview]]`, `[[lithium mine]]`. Commit. The file appears there; a click opens its source.
4. To remove a file: delete its name from `text.md`, commit, then delete the file and its row.

Commit in this order: media, `media.csv`, `text.md`. Each commit publishes on its own; this order keeps every one valid.

`media.csv` is required, even without media: keep only its first line. Names: unique, case-insensitive, no `[`, `]` or `|`. Source: a full `https://` link, or empty for your own material. A spreadsheet can save it as **CSV UTF-8**; commas or semicolons both work. Typing in GitHub: put a value containing a comma in double quotes.

Filenames: lowercase letters, digits, `.`, `_`, `-`. First character a letter or digit. No spaces. Example: `survey-photo.jpg`. References must match exactly, including case.

| Class | Formats | Maximum |
| --- | --- | --- |
| Text | `text.md` | 256 KiB |
| SVG | `.svg` | 5 MiB each |
| Image | PNG, JPG/JPEG, WebP, GIF, AVIF | 20 MiB each |
| Audio | MP3, M4A, WAV, OGG, AAC, FLAC | 20 MiB each |
| Video | MP4, WebM, MOV | 20 MiB each |
| Group | ≤ 100 files | 50 MiB total |

SVG: static, self-contained. No scripts, links, animation or external files. Only the main visual must be 1920 × 1080; extra images keep their own dimensions.

## 6. Check publication

Valid commits publish automatically, without approval. The site refreshes every ten minutes; delivery can take longer.

1. Open the website. Find your title. Check text, visual, links and media.
2. Not updated: open [publication results](https://github.com/Master-Interaction-Design-SUPSI/2026-ddd-making-sense-of-data/actions/workflows/pages.yml) → latest completed run on **main** → summary **Course publication** → row with your group identifier.

| Status | Meaning |
| --- | --- |
| `updated` | New version selected for this run. |
| `unchanged` | Same version as before. |
| `retained` | Update rejected; previous version kept. Read the explanation. |
| `skipped` | No valid published version yet. Correct and commit again. |
| `disabled`, `hidden`, `frozen` | Publication turned off or fixed by the course team. |

Published = run marked **verified** or **unchanged**. `updated` alone proves nothing. Run failed, unverified or pending; no row; no runs: contact the course team.

| Fault | Action |
| --- | --- |
| Wrong SVG size | Re-export the whole 1920 × 1080 frame. |
| Missing media | Upload the file, or correct its path in `media.csv` or `text.md`. Match case exactly. |
| `media.csv` required | Create `media.csv` at the root; first line `name,source,file`. |
| Not a name in `media.csv` | Add the row, or correct the name in `text.md`. |
| No row in `media.csv` | Every media file used in `text.md` needs a row, also when referenced by path. |
| Rejected update | Correct; commit to **main**. The next refresh retries. The previous version stays online meanwhile. |

## 7. Syntax

Prose: line breaks and blank lines between paragraphs become spaces, forming one continuous justified passage. Two trailing spaces or a trailing backslash also become a space. Headings, lists, blockquotes and code blocks stay separate; code keeps its line breaks. Never break a URL or filename across lines.

| Write in `text.md` | Result |
| --- | --- |
| `*Where and how is AI computation performed?*` | Research question: sans serif italic. |
| `**Data centres**` | Keyword or key concept: sans serif bold. |
| `{#116964\|Geology and ecology}` | Keyword or key concept: colored sans serif. |
| `{underline\|Dataset XX}` | Data source: underlined sans serif. |
| `[Dataset XX](https://example.org/data)` | Underlined data source; opens in a new tab. |
| `[[a detail\|A short explanation]]` | Note: `{✶ A short explanation}`. |
| `[[Parikka, 2015\|A geology of media\|type=bibliography]]` | Serif citation: `(■ Parikka, 2015. A geology of media)`. |
| `[[Author, year. Title\|https://example.org/source\|type=bibliography]]` | Serif linked citation; underlined on hover; opens the source in a new tab. |
| `[[a note\|More context\|type=note;color=green]]` | Green note. |
| `[[a quotation\|Quoted words\|type=quote;style=italic;color=crimson]]` | Crimson italic quotation. |
| `{crimson\|a key finding}` | Colored text. |
| `[[interview]]` | Media named in `media.csv`: inline image, audio or video; a click opens its source. |
| `[[the sketch\|media/example-detail.svg]]` | Inline image by path. The file still needs a row in `media.csv`. |
| `![A description](media/example-tall.svg)` | Inline image (Markdown). Same rule. |
| `[[a tone\|media/example-tone.mp3]]` | Inline audio by path. |
| `[[a video\|media/example-motion.mp4]]` | Inline video by path. |
| `[[a video\|media/example-motion.mp4\|source=https://example.org/original]]` | Video whose click opens this source instead of its `media.csv` source. Works for images and audio too. |
| `[![A description](media/example-detail.svg)](https://example.org/original)` | Image linked to its original source. |

Annotation form: `[[label|target|modifiers]]`. Modifiers are optional, separated by `;`, in any order.

| Modifier | Values |
| --- | --- |
| `type` | `note`, `bibliography`, `quote` |
| `style` | `italic`, `normal` |
| `color` | `crimson` or any CSS color, e.g. `#116964` |
| `source` | Original HTTP(S) source URL for an image, video or audio file. URLs with `;`, `\|`, `[` or `]` must encode those characters. |

- Note: open by default; `{✶ text}`; normal sans serif. `style=italic` explicitly opts into italic. The label toggles it.
- Citation (`type=bibliography`): inline serif, black, `(■ Author, year. Title)`. A URL target makes the whole citation a link to the original source. Black overrides every color. Text citations open by default; their label toggles the title.
- Quote: quotation marks on reveal.
- An explicit `color` overrides a surrounding `{color|…}` span; otherwise the span applies.
- `{color|✶ text}` renders in braces.
- Markdown `*italics*` works in prose and labels.
- Two-field annotations and emoji markers in the third field still work.
- Unknown, repeated or malformed modifiers stay visible as literal text. Correct them.
- Never put `|`, `[` or `]` inside a field.

## 8. Media behavior

| Media | Behavior |
| --- | --- |
| Image | Inline thumbnail; aspect ratio kept. Hover or keyboard focus: enlarged preview. Click or tap: opens the original source in a new tab. |
| Audio | Static player with a play symbol and label. Click or tap: opens the original source in a new tab. |
| Video | Inline, muted and looping; starts when half visible. Hover: enlarged preview with sound, when the browser permits playback. Keyboard focus: muted preview. Click or tap: opens the original source in a new tab. |
| External embed | Opens manually from its annotation. Fallback: **Open media on provider**. YouTube/Vimeo playback unverified. |

Use `source=` or a linked Markdown image to specify the original source. Without a source link, clicking opens the published media file itself. Original files and their original sources may have different URLs.

The course [media and sources worksheet](https://docs.google.com/spreadsheets/d/1WP-dlkyGFV2Ki1NTLo7auSYGrvrBxwdUBvVFZjOkV30/edit) is the working resource listed in *DDD-REPO-Commenti&Risorse.pdf*. Keep the source URL next to the matching media reference in `text.md`.
- Playback stops off screen, on entry switch, while the main image is enlarged, and when the page is hidden.
- Reduced motion: no autoplay, no preview animation.
- Reduced motion leaves the video still. Browsers may refuse automatic playback or sound; the source link remains available.
- Playback depends on file encoding and browser. Check your entry on the site.

## 9. Editor (preview)

Use only after the course team announces it. URL: website link + `editor/`.

1. **Group** → **Open last published version**. New group: **Start from template**.
2. Edit the Markdown. Attach files with their exact destination, e.g. `media/new-photo.png`, a name and a source link; the row goes into `media.csv`. **Insert in text** writes `[[name]]`.
3. **Check and prepare GitHub steps**. Resolve every error.
4. Execute the generated steps in order: compare current GitHub text, upload media, commit `media.csv`, commit `text.md`, delete removed files.
5. Replacing referenced media: use a new filename.
6. If shown, **Request publication** after all commits. Read the answer on the issue.

Drafts are saved in this browser only. Restore brings back text and attachments together. Storage denied or full: the editor lists what was not saved; a text-only backup needs its media reattached or discarded. Saving unavailable: **Download text.md** before leaving.

**WARNING**: A browser draft is not a commit. A completed checklist proves neither commit nor publication.
