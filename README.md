# learn-color-grading

An agent skill that teaches you photo editing by working from a reference image. You show a reference, get a didactic analysis of its composition, color, and mood, then send your own image and receive a technically deep, step-by-step guide to recreate the look in your editor of choice (Lightroom, Capture One, and others). After that, you iterate: send your result, get a precise technical comparison against the reference, and targeted corrections.

The goal is understanding, not recipes. Every recommendation explains what the tool does technically, why it's needed for the look, and what concretely changes in the image.

## How it works

The skill follows a four-phase workflow:

1. **Analyze the reference image**: Composition (depth layering, leading lines, light direction) and color/mood (palette, temperature contrast, saturation and contrast behavior, shadow coloring), built up didactically so you can transfer the principles to your own images.
2. **Diagnose your image against the reference**: A side-by-side comparison across the dimensions from [`skills/learn-color-grading/references/look-dimensions.md`](skills/learn-color-grading/references/look-dimensions.md): crop, black point, micro-contrast, shadow/highlight color, atmospheric depth, and more. It honestly names what already works and what can only be simulated.
3. **Step-by-step guide in your program**: Ordered global before local, coarse before fine: crop → white balance → exposure and dynamics → curve → color editor and color balance → local adjustments → detail → final polish. Every tool gets a starting value, how it works, what changes in your image, and how to check the dosage.
4. **Iteration**: You send back your result. The skill states precisely where the difference lies (black point, micro-contrast, saturation, shadow color…) and gives targeted corrections. If an earlier recommendation caused the deviation, it says so openly.

## Repository structure

```
skills/
├── learn-color-grading/
├────  SKILL.md                # Skill definition: rules, workflow, format
└────  references/
     └──  look-dimensions.md   # Checklist of dimensions in which looks differ
```

## Installation

### With the `skills` CLI (recommended)

Requires [Node.js](https://nodejs.org). The CLI detects your installed agents and copies the skill into the right directory.

**From GitHub:**

```bash
npx skills add adur1990/learn-color-grading
```

**From a local checkout:**

```bash
npx skills add /path/to/learn-color-grading
```

**Useful options:**

| Option | Effect |
|---|---|
| `-g` | Install globally (user-level, available in every project) |
| `-a <agent>` | Target specific agents, e.g. `-a claude-code -a opencode` |
| `--list` | Preview which skills the repo contains before installing |
| `-y` | Skip prompts (non-interactive / CI) |

Examples:

```bash
# Install globally for Claude Code and OpenCode, no prompts
npx skills add adur1990/learn-color-grading -g -a claude-code -a opencode -y

# See what's in the repo first
npx skills add adur1990/learn-color-grading --list
```

**Manage installed skills:**

```bash
npx skills list     # what's installed
npx skills update   # update all installed skills
```

### Manually

Copy this repository's folder into your agent's skills directory, e.g.:

```bash
# Claude Code (user-level)
cp -r learn-color-grading/skills/learn-color-grading ~/.claude/skills/

# Claude Code (project-level)
cp -r learn-color-grading/skills/learn-color-grading .claude/skills/

# OpenCode (project-level)
cp -r learn-color-grading/skills/learn-color-grading .opencode/skill/
```

The skill must end up as a folder containing `SKILL.md` (plus its `references/` directory) inside a directory your agent reads skills from.

## Usage

Once installed, just start using your editor agent naturally — the skill's description triggers automatically when it's relevant:

- **Show a reference image:** "Here's a photo I love — analyze the look for me."
- **Recreate a look:** attach your own image and a reference: "Get me this look in Lightroom."
- **Ask directly:** "How do I get this look?", "Why are my shadows too green?", "Compare my edit to the reference."
- **Iterate:** send your edited result — you'll get a technical comparison and targeted corrections.

The skill responds in your language and works with whatever program you name.

## License

[GPL-3.0](LICENSE).
