# Council of Gamgee

Your private advisory council of AI agents that debate strategic questions from competing analytical frameworks.

Seven specialized agents analyze your question independently, then argue with each other — making concessions, challenging assumptions, and producing a synthesis no single perspective could reach alone.

## What This Is

You bring a strategic question. The council debates it through seven lenses:

| Agent | Framework | What They Do |
|-------|-----------|-------------|
| **Kautilya** | Arthashastra | Power mechanics, statecraft, leverage, alliance strategy |
| **Shannon** | Information Theory | Signal vs noise, Bayesian reasoning, uncertainty quantification |
| **Girard** | Mimetic Theory | Hidden desires, rivalry dynamics, status games, scapegoat mechanisms |
| **Burt** | Structural Holes | Network topology, brokerage positions, who's connected to whom |
| **Musashi** | Book of Five Rings | Timing, decisive action, what to literally do Monday morning |
| **Adversary** | Red Team | Pre-mortem, hidden assumptions, ten reasons this fails |
| **Khaldun** | Muqaddimah | Historical cycles, rise and decline patterns, asabiyyah |

Plus a **Conductor** that carries all seven frameworks and synthesizes.

The agents don't just analyze in parallel — they **debate each other directly**, challenge assumptions, make concessions, and converge on recommendations that survive adversarial scrutiny.

## The Four Fundamental Forces

Every situation is decomposed into four primitive forces:

1. **Information Asymmetry** — who knows what others don't
2. **Network Concentration** — where connections cluster and power accrues
3. **Mimetic Desire** — people wanting what others want
4. **Entropy/Disequilibrium** — opportunity where things are out of balance

## Setup

### Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI installed and working

### Quick Install (let Claude do it)

Paste this into Claude Code:

> "Set up the council agents from https://github.com/gamgee-ai/council-of-gamgee — clone the repo, read the README, and install the agents. Enable the Agent Teams experimental flag in settings.json so the agents can debate each other."

Claude Code will read the repo, figure out the installation steps, and handle the rest. Allow it to modify your `~/.claude` directory when prompted.

### Manual Install

Create the agents directory if it doesn't exist, then copy the agent files:

```bash
git clone https://github.com/gamgee-ai/council-of-gamgee.git
mkdir -p ~/.claude/agents
cp council-of-gamgee/agents/*.md ~/.claude/agents/
```

Optionally, copy the frameworks reference doc:

```bash
cp council-of-gamgee/frameworks.md ~/.claude/agents/
```

That's it. The agents are now available as subagents in any Claude Code session. You can use them individually right away (see Usage below).

### Step 2: Enable Agent Teams (for multi-agent debate)

> **Note:** As of February 2026, Agent Teams is an experimental feature in Claude Code. The agents work individually without this flag, but for the full council debate experience (where agents message and challenge each other directly), you need to enable it.

Add the following to your Claude Code settings file at `~/.claude/settings.json`:

```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

If you already have content in that file, just merge the `env` block into your existing settings. Then restart Claude Code for the change to take effect.

### Usage

**Single agent** (any strategic question):

```
/council-kautilya What are the power dynamics in [situation]?
/council-adversary Red team my plan to [do something]
/council-musashi What do I literally do this week about [problem]?
```

**Full council debate** (Agent Teams):

Ask Claude Code to create a team and spawn all council members on your question:

> "Create a team with kautilya, shannon, girard, adversary, musashi, and burt. Have them debate: [your strategic question]. They should challenge each other directly and produce a synthesis."

The agents will:
1. Research independently (with web search)
2. Produce initial analyses from their framework
3. Message each other to debate
4. Make concessions and refine positions
5. Converge on a synthesized recommendation

A full council debate typically takes 5-10 minutes and produces 30-50+ cross-agent messages.

**Conductor** (single-agent synthesis):

```
/council [your question]
```

Or just say:

> "Council of Gamgee, [your question]"

The conductor carries compressed versions of all seven frameworks and selects the 3-4 most relevant for your question.

## Frameworks Reference

See [frameworks.md](frameworks.md) for the full analytical framework including:
- Four Fundamental Forces and their interactions
- Condensed methodology for each of the seven agents
- Force interaction table

## Examples

### Questions that work well

- "Should I keep building or start selling?"
- "Analyze the power dynamics in [industry/situation]"
- "I'm deciding between [option A] and [option B] — what am I not seeing?"
- "Red team my plan to [launch/build/invest in something]"
- "What is the current state of [market/geopolitical situation]?"
- "How should I position myself in [competitive landscape]?"

### What to expect

Each agent produces a genuinely different analysis — not just different words, but different conclusions drawn from different premises. The debate between them surfaces blind spots, challenges assumptions, and frequently changes the recommendation from what any single agent would have suggested.

## License

MIT
