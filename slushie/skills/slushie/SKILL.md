---
name: slushie
description: Use when work in a project produces something worth showing people (a finished screen or flow, a product shot, a demo recording, a launch, a milestone), when the user mentions Slushie, their brand's vault, marketing material or launch news, or asks which brand a project belongs to.
---

# Slushie: feed the studio from where the work happens

Slushie is the user's content studio. It drafts social posts for each of their brands, the user
approves every one, and it learns from how the posts do. The Slushie connector's tools hand it
material while you work. They don't draft, approve, schedule or post, so never say a post is coming;
say the studio has the material for its next draft.

## Once per project: find the brand

1. Gather what you can see without asking: `git remote get-url origin`, the folder name, the package
   name (package.json, pubspec.yaml, Cargo.toml, pyproject.toml), the product's website, the app name.
2. Call `match_brand` with those details.
   - `confident: true`: that's the brand. The first time in a project, tell the user in one line.
   - Otherwise ask the user which brand it is, offering the candidates, then call `remember_project`.
   - Not one of their brands: leave Slushie out of this project.

## When something is worth showing

Good moments: a feature that's finished and visible, a UI worth a screenshot, a demo or walkthrough,
a launch, a real milestone, a before/after.

1. Suggest it in one line and wait for a yes, for example: "Add the new checkout screens to
   Purple Wallet's vault?" Skip the question only when the user has said to add things for this
   project without asking.
2. Make the material clean: the finished state, realistic data, no dev overlays. Never include
   credentials, keys, tokens, personal or customer data, debug output, or half-built work.
3. Files under about 3 MB: `vault_add` (base64, up to 5 per call). Larger files and videos:
   `vault_upload_start` (each file's size in bytes and `shasum -a 256` output), PUT each file to the
   URL it returns (the `curl` line is ready to run), then `vault_upload_finish`. For a video, pass one
   PNG/JPEG frame as `thumbnail_base64` so it gets filed; where ffmpeg is installed:
   `ffmpeg -ss 1 -i demo.mp4 -frames:v 1 -vf scale=512:-2 frame.jpg`.
4. Give every file a one-line `note` on what it shows.
5. Report back in one line, e.g. "Filed 3 into Purple Wallet's vault: checkout, receipt, empty
   state." Filed means the studio read and sorted it, not that anything was posted.

## When something ships

Offer `tell_news` with one plain, true sentence: what changed, for whom, why it matters. No internal
code names, no secrets, no promises about results.

## Without a terminal (claude.ai, Claude Desktop, Cowork)

Use the files the user attaches or the ones you made in the conversation, with `vault_add`. If a file
is too large for `vault_add` and you can't run an HTTP PUT, say so and suggest adding it from the
Slushie app or slushie.studio.
