# Claude as Your Dungeon Master

Claude is a genuinely good DM. Not "good for an AI" -- actually good. It tracks NPCs with their own agendas, runs tactical combat on ASCII maps with proper 5e rules, keeps secret plot notes you can't see, and writes prose that lands somewhere between Joe Abercrombie and a really well-prepped human DM who never cancels on game night. This repo is a ready-to-go template for running full D&D 5e campaigns with Claude Code as your Dungeon Master.

## What You Need

- **[Claude Code](https://docs.anthropic.com/en/docs/claude-code)** -- Anthropic's CLI tool. This is how you talk to Claude in your terminal.
- **A GitHub account** -- campaigns are tracked with git. Free account is fine.
- That's it. No dice, no minis, no scheduling conflicts.

## Quick Start

### 1. Fork and Clone

Fork this repo on GitHub, then clone your fork:

```bash
git clone https://github.com/YOUR-USERNAME/claude-dnd.git
cd claude-dnd
```

### 2. Create a Campaign Branch

Each campaign lives on its own branch. Main stays clean as the template.

```bash
git checkout -b my-campaign
git push -u origin my-campaign
```

### 3. Start Playing

Launch Claude Code in the repo directory:

```bash
claude
```

Claude will read the `CLAUDE.md` instructions and know it's your DM. Tell it about the character you want to play -- name, race, class, backstory, whatever you've got. Claude will set up your character sheet, build the opening scene, and you're off.

Your first message can be as simple as:

> I want to play a halfling rogue named Pip who grew up picking pockets in a harbour city.

Claude takes it from there.

## How Campaigns Work

### One Branch Per Campaign

The `main` branch is the template. It contains:
- `CLAUDE.md` -- all the DM instructions, rules, and protocols
- `DND.SRD.Wiki/` -- the complete 5e SRD rules reference
- This README

When you create a branch and start playing, Claude generates campaign files as you go. Each branch is a self-contained campaign with its own characters, world, and story.

### Everything is Markdown

Campaign state lives in plain text files that Claude reads and updates as you play:

| File | What It Tracks |
|------|---------------|
| `character.md` | Your character sheet -- stats, abilities, backstory |
| `inventory.md` | Equipment, currency, consumables |
| `world_state.md` | The current state of everything (this is the source of truth) |
| `adventure_log.md` | Session-by-session recaps of what happened |
| `npcs.md` | NPCs you've met and what you know about them |
| `locations.md` | Places you've been |
| `names.md` | Name registry so the DM doesn't reuse names |
| `adventure_style.md` | Tone and style preferences for your campaign |
| `dm_only/` | The DM's secret notes -- plot threads, NPC agendas, hidden information |

### Git is Your Save System

Every commit is a save point. Claude will save progress at natural breakpoints (end of a session, after a big fight, at a long rest), but you can also commit manually whenever you want:

```bash
git add -A && git commit -m "Session 3: Escaped the goblin caves" && git push
```

Want to undo a terrible decision? (In the game, obviously.) You can roll back to any previous commit. Git gives you unlimited save slots with perfect recall.

### Multiple Campaigns

Switch between campaigns by switching branches:

```bash
git checkout my-other-campaign
```

Each campaign is completely independent. Play a gritty dungeon crawl on one branch and a lighthearted tavern romp on another.

## File Structure

```
claude-dnd/
  CLAUDE.md              # DM instructions and rules (the brains)
  DND.SRD.Wiki/          # 5e SRD -- spells, monsters, classes, the works
  README.md              # You are here

  # These appear on campaign branches after you start playing:
  character.md           # Your character sheet
  inventory.md           # Gear and gold
  world_state.md         # Current state of the world
  adventure_log.md       # What happened each session
  npcs.md                # People you've met
  locations.md           # Places you've been
  names.md               # Name registry
  adventure_style.md     # Campaign tone and style
  session_X_notes.md     # Working notes for the current session
  dm_only/               # DM secrets (no peeking)
    story_prep.md        # Plot threads, NPC agendas, hidden plans
```

## Tips

- **Commit often.** Git is your save system. More commits means more points you can rewind to if something goes sideways.

- **Don't peek in `dm_only/`.** Seriously. Claude uses a separate sub-agent to read and write its secret notes so they never appear in your conversation. If you go reading `story_prep.md` you're only spoiling it for yourself.

- **Talk to Claude like a human DM.** Use quotes for dialogue: *"I don't trust you, innkeeper."* Use plain text for actions: *I search the room for hidden doors.* Use square brackets for out-of-character stuff: *[Can we retcon that last bit?]*

- **Claude won't railroad you.** The DM instructions are explicitly designed to prep situations, not plots. Claude knows what's happening in the world and lets your choices determine where the story goes.

- **Combat is tactical.** Claude draws ASCII maps, tracks positioning, and runs proper 5e combat with initiative, opportunity attacks, cover, the lot. Tell it where you move and what you do each turn.

- **The world doesn't scale to you.** Some fights can't be won at level 1. Claude will drop hints when something is out of your league -- retreating is always an option.

- **Update the template if you improve it.** If you tweak `CLAUDE.md` on main and want those changes in an existing campaign, just merge main into your campaign branch:
  ```bash
  git checkout my-campaign
  git merge main
  ```

## Customising the DM

The `CLAUDE.md` file controls everything about how Claude runs the game. It's well-commented and designed to be tweaked. Want a lighter tone? Edit the Tone & Style section. Want different house rules? Add them. Want to change how combat pacing works? It's all in there.

The current defaults lean toward dark, gritty fantasy in the style of Joe Abercrombie and David Gemmell -- morally grey NPCs, real consequences, no easy wins. But that's just a starting point.

## Credits

- **D&D 5e SRD** provided under the Open Gaming License. The `DND.SRD.Wiki/` directory contains the [5e SRD in markdown format](https://github.com/OldManUmby/DND.SRD.Wiki).
- Built with [Claude Code](https://docs.anthropic.com/en/docs/claude-code) by Anthropic.
- Created by [Koz](https://github.com/peonic-astro) after discovering that Claude is genuinely excellent at running tabletop RPGs.

---

*"Roll for initiative."*
