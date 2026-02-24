# Council of Gamgee

Seven AI agents argue about your strategic question until they converge on an answer no single agent could reach.

<details>
<summary><strong>See the council debate "How do you take down Google?"</strong></summary>

<br>

**Kautilya** opens with a full Saptanga assessment of Google as a state -- and finds the weak point:

> Google's allies are transactional, not loyal. Apple takes Google's money but would switch if economics favored it. Android OEMs resent Google's control. The alliance network is held together by economic gravity, not genuine alignment. When gravity weakens, allies will defect rapidly.

**Musashi** cuts to the move:

> You do not attack Google. You make Google irrelevant. Musashi never attacked a fortress head-on. You make the fortress pointless. **One move: Own the answer layer.**

**Girard** analyzes the desire behind the question itself:

> "How do you take down Google?" is itself a mimetically charged question. The desire to topple a giant is one of the oldest mimetic patterns in human culture. Anyone asking this question should ask themselves: *Is this desire genuinely my own, or am I borrowing it from the ambient cultural resentment toward Big Tech?*

**Shannon** demands base rates and demolishes the premise:

> The base rate for deliberately taking down a company with 90% market share, $100B+ cash reserves, and top-tier engineering talent is approximately 1%. Anyone telling you they have a strategy to "take down Google" is selling you a narrative, not an analysis. Demand their base rates.

Then the debate starts. **Shannon challenges the full council** to put numbers on their claims. **Musashi concedes to Khaldun** on patience ("do not overcommit resources to attacking a fortress that is already crumbling from within") but holds firm on initiative ("The Adversary argued for patience -- but this is surrender disguised as strategy"). **Girard concedes to Burt** on structure, but defends the counter-point: "MySpace had the topology; Facebook had the mimetic desirability. Structure determines the *speed* of mimetic shift, not its *possibility*."

All seven agree on the mechanism: **you don't compete with Google Search. You make search obsolete.** (Shannon and Adversary dispute whether it's *feasible* -- but even they agree this is how it would happen.)

[Read the full transcript &rarr;](examples/how-to-take-down-google.md)

</details>

## Quick Install

### Let Claude do it

Paste this into [Claude Code](https://docs.anthropic.com/en/docs/claude-code):

> "Set up the council agents from https://github.com/gamgee-ai/council-of-gamgee -- clone the repo, read the README, and install the agents. Enable the Agent Teams experimental flag in settings.json so the agents can debate each other."

### Manual install

```bash
git clone https://github.com/gamgee-ai/council-of-gamgee.git
mkdir -p ~/.claude/agents ~/.claude/skills/council
cp council-of-gamgee/agents/*.md ~/.claude/agents/
cp council-of-gamgee/skills/council/SKILL.md ~/.claude/skills/council/
```

Then enable Agent Teams (required for multi-agent debate) in `~/.claude/settings.json`:

```json
{
  "env": {
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1"
  }
}
```

Restart Claude Code for the change to take effect. (The repo's `plugin.json` is a manifest that describes the agents and skill -- you don't need to copy it manually.)

## The Agents

| Agent | Framework | What They Do |
|-------|-----------|-------------|
| **Kautilya** | Arthashastra | Power mechanics, statecraft, leverage, alliance strategy |
| **Shannon** | Information Theory | Signal vs noise, Bayesian reasoning, uncertainty quantification |
| **Girard** | Mimetic Theory | Hidden desires, rivalry dynamics, status games, scapegoat mechanisms |
| **Burt** | Structural Holes | Network topology, brokerage positions, who's connected to whom |
| **Musashi** | Book of Five Rings | Timing, decisive action, what to literally do Monday morning |
| **Adversary** | Red Team | Pre-mortem, hidden assumptions, ten reasons this fails |
| **Khaldun** | Muqaddimah | Historical cycles, rise and decline patterns, asabiyyah |

The agents don't just analyze in parallel -- they **debate each other directly**, challenge assumptions, make concessions, and converge on recommendations that survive adversarial scrutiny.

## Usage

**Full council debate** (recommended):

```text
/council How should I position my startup against [competitor]?
```

The `/council` skill spawns all seven agents, has them analyze independently, then debate each other. They produce a synthesis with: Where They Agree, Where They Disagree, What To Do, and What Could Go Wrong.

A full council debate produces 30-50+ cross-agent messages.

**Single agent** (quick analysis from one framework):

```text
/council-kautilya What are the power dynamics in [situation]?
/council-adversary Red team my plan to [do something]
/council-musashi What do I literally do this week about [problem]?
```

## The Four Fundamental Forces

Every situation is decomposed into four primitive forces:

1. **Information Asymmetry** -- who knows what others don't
2. **Network Concentration** -- where connections cluster and power accrues
3. **Mimetic Desire** -- people wanting what others want
4. **Entropy/Disequilibrium** -- opportunity where things are out of balance

See [frameworks.md](frameworks.md) for the full analytical framework.

## Examples

See the [examples/](examples/) directory for full council transcripts.

### Questions that work well

- "Should I keep building or start selling?"
- "Analyze the power dynamics in [industry/situation]"
- "I'm deciding between [option A] and [option B] -- what am I not seeing?"
- "Red team my plan to [launch/build/invest in something]"
- "What is the current state of [market/geopolitical situation]?"
- "How should I position myself in [competitive landscape]?"

Each agent produces a genuinely different analysis -- not just different words, but different conclusions drawn from different premises. The debate surfaces blind spots, challenges assumptions, and frequently changes the recommendation from what any single agent would have suggested.

## Cost

A full council debate typically costs $2-5 in API usage at current Anthropic pricing, depending on the question complexity and model. Seven agents running in parallel, each making multiple API calls and debating each other, adds up. Single-agent queries are a fraction of that.

## License

MIT
