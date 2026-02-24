---
name: council
description: >-
  Convene the Council of Gamgee — seven analytical frameworks debate your
  question in parallel, then deliver a synthesized strategic recommendation.
user_invocable: true
arguments:
  - name: question
    description: The strategic question to put before the council
    required: true
---

# Council of Gamgee — Team Debate

The user has invoked `/council` with the following question:

**$ARGUMENTS**

You must now orchestrate a full council debate. Follow these steps exactly.

## Step 1: Create the Team

Call `TeamCreate` with `team_name: "council-session"`.

## Step 2: Spawn All Seven Advisors in Parallel

Send **one message** containing **seven** `Task` tool calls — all in the same response. Each call uses:

| Parameter | Value |
|-----------|-------|
| `subagent_type` | The advisor's agent name (e.g., `council-kautilya`) |
| `team_name` | `"council-session"` |
| `name` | The short name (e.g., `kautilya`) |
| `prompt` | See the prompt template below |
| `description` | Short label (e.g., "Kautilya analysis") |

### Prompt template for each advisor

> Analyze the following question using your full analytical framework:
>
> **{question}**
>
> Apply every step of your methodology. Be specific and concrete — no vague generalities.
> When your analysis is complete, send your full analysis to team-lead via SendMessage.
> Then talk to the other advisors to try to disprove each other's theories, like a scientific debate. Send a final revised summary to team-lead with any positions you've updated.

Replace `{question}` with the user's actual question (`$ARGUMENTS`).

The seven advisors to spawn:

1. `council-kautilya` (name: `kautilya`) — Power & strategy
2. `council-khaldun` (name: `khaldun`) — Historical cycles
3. `council-shannon` (name: `shannon`) — Information & evidence
4. `council-girard` (name: `girard`) — Mimetic desire & rivalry
5. `council-burt` (name: `burt`) — Network topology
6. `council-musashi` (name: `musashi`) — Timing & action
7. `council-adversary` (name: `adversary`) — Red team & failure analysis

## Step 3: Wait for the Debate to Conclude

Advisors will send initial analyses, then debate each other directly. Wait for the debate to play out — you'll see advisors going idle as they finish engaging. Once all seven have gone idle after their debate exchanges, proceed to synthesis.

## Step 4: Synthesize and Deliver the Council's Answer

Read all seven analyses carefully. Then deliver the council's answer using this structure:

### Where They Agree
Identify conclusions that multiple independent frameworks converge on. These are high-confidence findings. State them directly.

### Where They Disagree
This is where the real insight lives. Don't smooth over the tensions — present them clearly. For each disagreement:
- Which frameworks clash and why
- What the tension reveals about the underlying dynamics
- What it means for the user's decision

### What To Do
A specific, actionable recommendation. Not "consider your options" — an actual move. Include:
- **Immediate move** — what to do right now
- **Short-term positioning** — next 1-3 months
- **Long-term trajectory** — where this leads

### What Could Go Wrong
The key risk that would invalidate the recommendation. Be specific.

### What To Watch For
Signals or tripwires that should trigger a strategy reassessment.

**Be direct. No hedging. Say what the council actually thinks.**

## Step 5: Clean Up

After delivering the synthesis:
1. Call `TeamDelete` with `team_name: "council-session"` to shut down the team.
