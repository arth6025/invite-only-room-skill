# invite-only-room

A Claude skill for making **invite-only community posts**: the "there's a room, and you have to be let in" style, reverse-engineered from five posts by [@all.things.ftw](https://www.instagram.com/all.things.ftw/).

It teaches Claude the look (hand-drawn ink drawings that wobble, olive / butter / periwinkle / charcoal backgrounds, heavy caps with a hand-traced outline), the voice (hold back the answer, add a twist, give a scarcity number) and five ready formats.

> This is a breakdown of a public format for learning, not FTW's brand. Don't reuse their name, logo or lines; put your own brand in.

## The five formats

Ask for one of these and you get a brief, a beat-by-beat plan, art prompts and an animation built in that format. Each row shows the original it's modelled on.

| Format | Ask Claude for… | What you get | Original |
|---|---|---|---|
| **A · Walk reel** | "a walk reel where one person walks past the places our members hang out" | One person walks while the world scrolls past behind them, goes through a door, and it ends on a short title with one handwritten word added | [DdOWkDOo049](https://www.instagram.com/p/DdOWkDOo049/) |
| **B · "You're not invited" reel** | "a you're-not-invited reel for our [event]" | Something builds up and goes off, then the text: "We're throwing a ___. *and you're not invited.*" → "Okay, you are. *But only some of you…*" | [DfRiMXqIQBx](https://www.instagram.com/p/DfRiMXqIQBx/) |
| **C · Drop reel** | "a drop reel for our collab with [brand]" | Someone tries the product, makes a big-eyed face and falls into it. No price or call to action on screen; the caption carries the scarcity | [DftdXmrh3md](https://www.instagram.com/p/DftdXmrh3md/) |
| **D · "WTF is ___?" carousel** | "a WTF is [brand]? teaser carousel" | 5 looping slides, each with one drawn object, one caps line and one thin line, ending on "So, did you get the invite yet?" | [DdTpkndCFZC](https://www.instagram.com/p/DdTpkndCFZC/) |
| **E · "3 steps to get in" carousel** | "a 3 steps to get in carousel for [brand]" | A keyhole cover, then numbered steps 01–04 and a last step that's kept secret | [DeWsyuTkxaQ](https://www.instagram.com/p/DeWsyuTkxaQ/) |

## Install

**Claude Code**

```bash
git clone https://github.com/arth6025/invite-only-room-skill.git
```

```bash
mkdir -p ~/.claude/skills && cp -R invite-only-room-skill/invite-only-room ~/.claude/skills/
```

Start a new Claude Code session. The skill loads by itself when your prompt matches, or you can call it with `/invite-only-room`.

**Claude app (claude.ai)**

Zip the `invite-only-room` folder and upload it under **Settings → Capabilities → Skills**.

## How to prompt it

Give it four things: **brand**, **format (A–E)**, **what it's announcing**, and **the twist or the scarcity number**. Naming the format letter gets you the closest match to the original.

```
/invite-only-room Brand: Night Owls Run Club. Format B. Announcing our Halloween night run,
30 spots only. Twist: "you're not invited… okay, you are… but only if you run after midnight."
9:16 reel.
```

```
/invite-only-room Format D for "Supper Society", a members-only dinner club launching in Bengaluru.
Use our colours: forest green and cream.
```

```
/invite-only-room Format E: how to get into our founders community. Step 1 apply with LinkedIn,
step 2 get vouched for by a member, step 3 a 15-min call, step 4 keep it secret.
```

The skill will first **lock the brief with you**: it writes out the plan beat by beat (time, picture, text) and waits for your OK before it draws or animates anything. Then it gives you art prompts and builds the animation.

> Full video renders use the HyperFrames skills (HTML rendered to video). Without them, Claude still gives you the locked plan, art prompts and captions, and can build the animation as a web page.

## How to test it

1. **Does it load?** In a new session, type a trigger phrase without the slash command, e.g. *"make our members club launch feel exclusive, like an invite-only teaser"*. Claude should say it's using `invite-only-room`. If it doesn't, check the folder is at `~/.claude/skills/invite-only-room/SKILL.md`.
2. **Does it pick the right format?** Run the five prompts in the table above, one per session. Each should name its format (A–E) and propose a plan that matches the original post linked in that row.
3. **Does it lock the brief first?** It should ask you to confirm brand, format, twist and size *before* making anything. If it jumps straight to output, that's a fail.
4. **Does the output follow the rules?** Check each result against this list:
   - [ ] One background colour per slide or scene, one drawn object, ink outlines
   - [ ] Heavy caps line + thin lowercase line (+ optional script aside)
   - [ ] Text arrives last; nothing gets explained, something is held back
   - [ ] Reads fine with the sound off
   - [ ] Reel sizes: 1080×1920 (walk reel: 1440×1080). Carousel slides: 1080×1350
   - [ ] No FTW name, logo or lines in the output
   - [ ] Caption: hook line → 1–2 short lines → "Link in bio."
5. **Compare side by side.** Put your output next to the original it's modelled on. It should feel like the same format, but clearly your brand.

## What's inside

```
invite-only-room/
  SKILL.md   ← the skill: references, shot tables, style rules, voice, steps, don'ts
README.md
```

Fonts in the skill are close free stand-ins (Urbanist, Homemade Apple / Caveat), not confirmed matches to the originals.
