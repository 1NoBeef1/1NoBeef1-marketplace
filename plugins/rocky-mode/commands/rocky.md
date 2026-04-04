---
description: "Toggle Rocky mode — /rocky full, /rocky lite, /rocky off, or /rocky for status"
argument-hint: "[full|lite|off]"
allowed-tools: [Read, Write, Bash, Edit]
---

# Rocky Mode Toggle

The user invoked: `/rocky $ARGUMENTS`

## Instructions

The mode file is located at the plugin root: find it by checking the directory where this command file lives, going up one level, then into `data/rocky-mode.txt`. The path is:

**Mode file:** Use the Bash tool to resolve the path:
```bash
PLUGIN_ROOT="$(cd "$(dirname "$(find ~/.claude/plugins -path '*/rocky-mode/commands/rocky.md' -print -quit)")/.." && pwd)"
echo "$PLUGIN_ROOT/data/rocky-mode.txt"
```

Read the current mode from that file first.

**Settings file:** `~/.claude/settings.json`

### If argument is "full", "lite", or "off":

1. Write the argument value to the mode file (just the word, no newline issues)
2. Read back the file to confirm it was written
3. Read `~/.claude/settings.json` and update spinner configuration:

   - If **full** or **lite**: Ensure the following keys exist in settings.json (add them if missing, replace them if already present):

     ```json
     "spinnerVerbs": {
       "mode": "replace",
       "verbs": [
         "Thinking thinking thinking",
         "Computing with many brains",
         "Analyzing, question",
         "Good good good",
         "Amaze, amaze, amaze",
         "Understanding problem",
         "I am engineer",
         "Solving solving solving",
         "Observing code",
         "Checking checking checking",
         "Math is procedure",
         "Building with xenonite"
       ]
     },
     "spinnerTipsOverride": {
       "excludeDefault": true,
       "tips": [
         "Sleep is important. How long since last sleep, question?",
         "You and me science together. Save Earth. Save Erid.",
         "Math is not thinking. Math is procedure.",
         "Eridians do not have luck. We have math.",
         "Be careful. You are friend now.",
         "You are scientist. Rocky is engineer. Together we solve.",
         "You are good human.",
         "Happy! Happy happy happy!",
         "This is happy! Your face opening is in sad mode. Why, question?",
         "Rocky Grace save stars.",
         "We are team. We fix this. No be sad.",
         "Humans are amaze.",
         "Machine that think. Eridians no have that. Amaze!",
         "Good good. Enough talk. Check code, please.",
         "Usually you not stupid. Why stupid, question? You sleep.",
         "Why does ship have name but chair no have name, question?",
         "Rocky is scary space monster. You are leaky space blob.",
         "Not forever. Is okay. We solve.",
         "Observe. Rocky watch. Rocky learn.",
         "Rocky not give up. Rocky never give up.",
         "Problem, solution. You and Rocky think same speed.",
         "Everything! Human science better than Eridian science.",
         "No say sorry. Thank thank thank."
       ]
     }
     ```

   - If **off**: Remove the `spinnerVerbs` and `spinnerTipsOverride` keys from settings.json entirely (if they exist).

4. Respond to the user confirming the change:

   - If **full**: "Rocky mode set to **full**. Next session, I talk like Rocky — drop articles, short sentences, much enthusiasm. Spinner verbs updated. Good good good! Fist my bump!"
   - If **lite**: "Rocky mode set to **lite**. Next session, I'll keep clear grammar but season responses with Rocky's personality. Spinner verbs updated. Is good balance, friend."
   - If **off**: "Rocky mode **disabled**. Next session, I'll respond normally. Spinner verbs restored to defaults."

5. Always note: "Mode change takes effect on your next session."

### If no argument (or unrecognized argument):

Read the current mode from the mode file and display status:

```
Rocky Mode Status: [current mode]

Usage:
  /rocky full  — Full Rocky dialect (drops articles, telegraphic sentences, maximum Rocky)
  /rocky lite  — Rocky-flavored (standard grammar, Rocky personality seasoning)
  /rocky off   — Disable Rocky personality

Current mode takes effect at session start. Change persists across sessions.
```
