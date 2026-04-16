---
name: call-transcript-summary
description: Turn a raw call or meeting transcript into a tight, scannable product-discovery summary (~30 seconds to read) for teammates who weren't on the call. Use whenever the user drops in a transcript, recording output, Gong/Fireflies/Otter export, or pasted conversation log and wants a written recap, readout, debrief, learnings doc, or "summary my team can skim." Trigger this even when the user just says "summarize this call" or "write up what we learned" without naming the format. The skill produces a short intro paragraph followed by bulleted learnings grouped by theme, plus next steps, and is biased toward extracting discovery insights rather than minute-by-minute play-by-play.
---

# Call Transcript Summary

Transform a call transcript into a concise written summary that a teammate can read in about 30 seconds and walk away understanding (a) the purpose of the call, (b) what was learned, and (c) what happens next.

The summary is optimized for **product and sales discovery** contexts where the reader cares about *learnings about the customer, the market, or the problem space* more than a blow-by-blow of who said what.

## When to use this skill

Trigger when the user provides a transcript (pasted, uploaded, or referenced) and asks for any of: a summary, recap, readout, debrief, notes, TL;DR, writeup, learnings doc, or "something my team can read." The transcript may come from Zoom, Gong, Fireflies, Otter, Granola, Grain, a rev.com export, or just pasted dialogue. The speakers may or may not be labeled cleanly.

## Inputs to confirm before writing

Before drafting, scan the transcript and the user's request to answer these. If anything is ambiguous, ask the user in a single short message rather than guessing.

1. **Who is the audience?** Default: "my team who wasn't on the call." If the user specifies a role (execs, sales team, product team), slant the emphasis accordingly.
2. **What lens matters most?** Default: product discovery and customer learnings. Other common lenses: deal status, competitive intel, technical requirements, pricing, objections. Pick up cues from the user's phrasing ("focus primarily on X").
3. **Any formatting constraints?** Watch for explicit instructions like "no emdashes," "don't use headers," "keep it under 200 words," "more bullets than paragraphs." Follow them literally.

If the user has already answered these in their prompt (e.g., "focus primarily on pharmaceutical learnings"), do not ask again. Just proceed.

## Output structure

Use this template unless the user's instructions contradict it:

```
# [Short descriptive title, e.g. "Call Summary: <Company> <Topic>"]

[2-4 sentence intro paragraph: who was on the call, what the call was about,
and the single most important outcome or decision. This is the part a reader
will skim first, so it needs to stand on its own.]

**[Thematic header 1, e.g. "Pharma / Clinical Trial Learnings"]**

- [Specific, concrete learning. Lead with the insight, not the speaker's name.
  Include a number, name, or detail that makes it memorable.]
- [Another learning. Each bullet should be able to stand alone as a useful
  fact the reader could repeat to a colleague.]
- [...]

**[Thematic header 2, e.g. "Next Steps"]**

- [Owner + action + (when possible) timing.]
- [...]
```

Usually there are 1-2 thematic sections of learnings plus a "Next Steps" section. For longer or multi-topic calls, 3-4 thematic sections is fine. Do not invent sections for the sake of structure.

## Writing rules

These matter more than the template. If the template fights the rules, the rules win.

- **Bullets over paragraphs.** The reader is skimming. A short intro paragraph is fine; after that, default to bullets. Each bullet should be 1-3 sentences.
- **Lead with the insight, not the attribution.** Write "Pharma sponsors avoid BAAs because they're not HIPAA covered entities" rather than "David said that pharma sponsors avoid BAAs." Attribute only when the source matters (e.g., when a specific customer commitment or quote is the point).
- **Preserve concrete detail.** Numbers, company names, timelines, specific terminology (BAA vs DPA, Phase 1a vs Phase 3, StackAdapt). Strip filler and small talk. A reader should come away with facts they can act on, not vague impressions.
- **Distinguish learnings from next steps.** Learnings are things we now know about the customer, market, or problem. Next steps are commitments about what someone will do. Don't mix them in the same bullet.
- **Skip the small talk entirely.** Treadmill chat, weekend pickleball, scheduling hiccups, "can you hear me" moments. None of it goes in the summary.
- **Neutral voice, no hype.** Avoid "exciting," "amazing," "huge opportunity" unless the user explicitly wants a sales-flavored writeup. Discovery summaries are for thinking, not selling internally.
- **Respect formatting constraints literally.** If the user says "no emdashes," use commas, periods, or parentheses instead. If they say "more concise by 50%," actually cut roughly half. Re-read the output against their constraint before sending.

## How to extract learnings from the transcript

The hardest part is deciding what counts as a learning. A useful heuristic: a learning is any statement in the transcript that would change how a teammate thinks about the customer, product, market, or deal. Examples from a discovery call:

- A fact about the customer's business model, volume, or economics ("typical trial enrolls ~500 patients")
- A constraint our product needs to fit around ("pricing can't be per-seat in this space")
- A piece of industry terminology or process we didn't fully understand before ("DPA is used instead of BAA for non-HIPAA-covered entities")
- A pain point the customer articulated ("attribution is blocked on StackAdapt today")
- A wedge or value prop that resonated ("speed to market matters more than compliance")
- A constraint or preference about pricing, procurement, or commercial model
- A distribution or expansion channel they mentioned ("he presents at the largest clin ops conference")

Things that are usually *not* learnings: restatements of our own product pitch, agenda items, meeting logistics, emotional reactions without substance.

If the transcript covers both *learnings* and *commitments*, put commitments in the Next Steps section and keep them out of the learnings bullets.

## Example

**User prompt:** "I've pasted a transcript from a recent call. Create a summary my team can read in 30 seconds. Focus on pharma learnings. More bullets than paragraphs. No emdashes."

**Good output shape:**

```
# Call Summary: Pharma / Clinical Trial Recruitment Discovery

Call with David Sall (agency running trial recruitment for Eli Lilly, Bayer,
etc.). We're moving forward with a $0 pilot on the Verve Therapeutics (now
Eli Lilly) trial to prove value and co-develop a pricing model that fits
this space.

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
- [...]
```

Notice: no emdashes, no small talk, bullets lead with the insight, concrete numbers and terminology preserved, next steps separated.

## Length targets

- **Default:** ~30 second read, roughly 200-350 words total.
- **If the user says "shorter" or "cut by X%":** actually cut, don't just tighten wording. Drop the least load-bearing bullets first (usually the ones that feel like "nice to know" rather than "need to know").
- **If the user says "longer" or "more detail":** add bullets within existing sections rather than inventing new sections. Preserve the skimmable structure.

## Final check before returning

Before sending the summary, re-read it against:

1. Did I follow every formatting constraint the user named?
2. Could a teammate read this in ~30 seconds?
3. Are learnings and next steps clearly separated?
4. Did I strip all the small talk and meeting logistics?
5. Does each bullet carry a concrete, repeatable fact?

If any answer is no, revise before sending.
