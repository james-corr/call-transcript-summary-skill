# Call Transcript Summary

A Claude skill that turns a raw call or meeting transcript into a tight, scannable summary your team can read in about 30 seconds.

Built for product discovery, sales discovery, and customer research calls, where the reader cares about *what we learned* more than a blow-by-blow of who said what.

## What it does

Drop in a transcript (from Zoom, Gong, Fireflies, Otter, Granola, Grain, or just pasted dialogue) and ask Claude to summarize it. The skill produces:

- A short intro paragraph with who was on the call and the key outcome
- Bulleted learnings grouped by theme
- A separate Next Steps section with owners and actions

It strips small talk and meeting logistics, leads bullets with the insight rather than the speaker, and preserves concrete details (numbers, names, terminology).

## Example

**You say:**
> Here's a transcript from a discovery call. Summarize it for my team, focus on pharma learnings, more bullets than paragraphs, no emdashes.

**Claude produces:**

```
# Call Summary: Pharma / Clinical Trial Recruitment Discovery

Call with David Sall (agency running trial recruitment for Eli Lilly, Bayer,
etc.). We're moving forward with a $0 pilot on the Verve Therapeutics trial
to prove value and co-develop a pricing model that fits this space.

**Pharma / Clinical Trial Learnings**

- Volume is far lower than our usual customers. A typical trial runs ~400
  monthly tracked users; even Phase 3 often enrolls only ~500 patients total.
- Our standard pricing does not fit. Built for high-volume health systems,
  it needs to be restructured around trials.
- BAAs are the wrong instrument. Pharma sponsors are not HIPAA covered
  entities and actively avoid the designation. We use a DPA instead.
- [...]

**Next Steps**

- Josh to build a one-pager with architecture and visuals.
- David routes it to Eli Lilly's clin ops tech lead.
```

## Installation

### Option 1: Install from the packaged `.skill` file

1. Download the latest `call-transcript-summary.skill` file (see Releases, or build it yourself with the instructions below).
2. In Claude.ai, go to **Settings → Capabilities → Skills**.
3. Upload the `.skill` file.

### Option 2: Build the `.skill` file yourself

If you've cloned this repo and want to package it (for example after editing the skill):

```bash
# Clone Anthropic's skill-creator repo if you don't have it
git clone https://github.com/anthropics/skills.git

# From the skill-creator directory, package this skill
cd skills/skill-creator
python -m scripts.package_skill /path/to/this/repo/call-transcript-summary
```

This produces `call-transcript-summary.skill`, which you can then upload in Claude's settings.

## Usage

Once installed, just paste a transcript and ask for a summary. The skill triggers on natural phrasing like:

- "Summarize this call"
- "Write up what we learned"
- "Give me a readout I can send to the team"
- "Debrief this for me"

You can steer the output by adding:

- **A lens:** "focus on pricing objections" or "focus on technical requirements"
- **Formatting constraints:** "no emdashes," "more bullets than paragraphs," "keep it under 200 words"
- **Audience:** "for my exec team" or "for engineering"

## Repo structure

```
call-transcript-summary/
├── README.md                         # You are here
├── LICENSE                           # MIT
├── call-transcript-summary/          # The skill itself (upload this folder, or the packaged .skill)
│   └── SKILL.md
└── examples/
    └── example-output.md             # Sample output
```

## Customizing

The skill is a single `SKILL.md` file. Open `call-transcript-summary/SKILL.md` and edit it directly. Common tweaks:

- Change the default length target (currently ~30 second read / 200-350 words)
- Add thematic sections specific to your domain (e.g., "Competitive Intel," "Pricing Signals")
- Adjust the "what counts as a learning" heuristic for your team's context

After editing, repackage with the command in Option 2 above.

## License

MIT. See `LICENSE`.

## Contributing

Issues and PRs welcome. If you build a variant of this skill for a different context (support calls, user interviews, investor meetings), consider opening a PR to add it as a sibling folder.
