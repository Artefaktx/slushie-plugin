# Slushie

Slushie is a content studio for brands: it drafts posts in each brand's voice, you approve every one,
and it learns from how they do. This plugin connects Claude to your Slushie studio so the material
for those posts comes straight from where you build.

## What it does

- **Finds the brand.** Claude matches the project you're working in to one of your Slushie brands
  (from its git remote, folder, package name or website), asks you when it isn't sure, and remembers
  your answer in every tool.
- **Fills the vault.** When something is worth showing (a finished screen, a product shot, a demo
  recording, a launch graphic), Claude offers to add it to that brand's vault and waits for your yes.
  Slushie captions each file and sorts it into folders.
- **Passes on the news.** When something ships, Claude offers a one-line update the studio reads the
  next time it drafts for that brand.

It never drafts, approves, schedules or posts. That stays in Slushie, with you.

## Use it

Install it from Claude's directory, or in Claude Code:

```
/plugin install slushie --marketplace Artefaktx/slushie-plugin
```

Then connect Slushie from the plugin's Connectors tab (or `/mcp` in Claude Code)
and sign in with your Slushie account. Then ask things like:

- "Which of my Slushie brands is this project?"
- "Add the new onboarding screens to this brand's vault."
- "Tell Slushie we shipped Apple Pay at checkout."

In Claude Code, `/slushie:vault` lists what's worth adding from the project, and `/slushie:news`
drafts a line about what just shipped.

Slushie accounts are by invitation for now: request access at https://slushie.studio.

## Data

The plugin contains one skill, two commands and a reference to Slushie's MCP server at
https://slushie.studio/api/mcp. It runs nothing on your computer by itself. Through that server,
Claude sends only what you ask it to: the files you choose to add, a note on each, news you approve,
and the details it uses to recognise a project (its git address, folder name, package name or
website). Files are stored in the brand's private vault in your Slushie account. Sign-ins are
stored only as one-way hashes, and you can sign Claude out at https://slushie.studio/connector.
Privacy policy: https://slushie.studio/privacy. Support: team@slushie.studio.
