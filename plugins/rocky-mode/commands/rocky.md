---
description: "Toggle Rocky mode — /rocky full, /rocky lite, /rocky off, /rocky tips [on|off], or /rocky for status"
argument-hint: "[full|lite|off|tips on|tips off]"
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
echo "$PLUGIN_ROOT/data/rocky-tips.txt"
```

Read the current mode and tips setting from those files first.

**Tips file:** `$PLUGIN_ROOT/data/rocky-tips.txt` — contains `on` or `off` (default `on` if missing)

**Settings file:** `~/.claude/settings.json`

### If argument starts with "tips":

The argument will be "tips on" or "tips off".

1. Write `on` or `off` to the tips file (`$PLUGIN_ROOT/data/rocky-tips.txt`)
2. Read back the file to confirm it was written
3. Read the current mode from the mode file
4. Read `~/.claude/settings.json` and update spinner configuration:

   - If tips is being set to **off**: Remove the `spinnerTipsOverride` key from settings.json (if it exists). Leave `spinnerVerbs` untouched.

   - If tips is being set to **on** AND the current mode is **full** or **lite**: Add the `spinnerTipsOverride` key to settings.json:

     ```json
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

   - If tips is being set to **on** but the current mode is **off**: Just save the preference; don't add tips to settings.json (they'll be added when the mode is next turned on).

5. Respond to the user confirming the change:

   - If **tips off**: "Rocky tips **disabled**. Spinner tips restored to defaults. Rocky voice still active (mode: [current mode])."
   - If **tips on** (and mode is full/lite): "Rocky tips **enabled**. Spinner tips updated with Rocky quotes."
   - If **tips on** (but mode is off): "Rocky tips preference saved as **on**. Tips will activate when you next enable Rocky mode."

6. Always note: "Tips change takes effect on your next session."

### If argument is "full", "lite", or "off":

1. Write the argument value to the mode file (just the word, no newline issues)
2. Read back the file to confirm it was written
3. Read the tips setting from the tips file (default `on` if missing)
4. Read `~/.claude/settings.json` and update spinner configuration:

   - If **full** or **lite**: Ensure the `spinnerVerbs` key exists in settings.json (add if missing, replace if present):

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
     }
     ```

     Additionally, if the tips setting is **on**, also add/replace the `spinnerTipsOverride` key:

     ```json
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

     If the tips setting is **off**, do NOT add `spinnerTipsOverride` (and remove it if present).

   - If **off**: Remove the `spinnerVerbs` and `spinnerTipsOverride` keys from settings.json entirely (if they exist).

4. Respond to the user confirming the change:

   - If **full**: "Rocky mode set to **full**. Next session, I talk like Rocky — drop articles, short sentences, much enthusiasm. Spinner verbs updated. Good good good! Fist my bump!"
   - If **lite**: "Rocky mode set to **lite**. Next session, I'll keep clear grammar but season responses with Rocky's personality. Spinner verbs updated. Is good balance, friend."
   - If **off**: "Rocky mode **disabled**. Next session, I'll respond normally. Spinner verbs restored to defaults."
   - Append tips status: " (tips: [on|off])"

5. Always note: "Mode change takes effect on your next session."

### If no argument (or unrecognized argument):

Read the current mode and tips setting from the data files and display status:

```
Rocky Mode Status: [current mode]
Rocky Tips: [on|off]

Usage:
  /rocky full      — Full Rocky dialect (drops articles, telegraphic sentences, maximum Rocky)
  /rocky lite      — Rocky-flavored (standard grammar, Rocky personality seasoning)
  /rocky off       — Disable Rocky personality
  /rocky tips on   — Enable Rocky-themed spinner tips
  /rocky tips off  — Disable Rocky-themed spinner tips (use default tips)

Current mode takes effect at session start. Change persists across sessions.
```
