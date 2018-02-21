---
title: "Cogs: Dice"
summary: "The Dice cog implements various dice rolls and other randomness-based functions."
last_updated: 21 February 2018
---

## 1. roll

Rolls dice.

Rolls a <sides>-sided die <num> times, and reports the rolls and total.

**Usage:** `.roll <num>d<sides>`

Arguments:
* `<num>`: Number of dice to roll.
* `<sides>`: Number of sides for each die.
* Do **not** include spaces between the arguments and the `d`.

**Channels:** #tabletop, #bot_test

**Usable By:** Anyone

**Example:**
* `.rolls 3d6` - Roll three six-sided dice.


## 2. rollf

Rolls four dice for the FATE tabletop roleplaying game system.

**Usage:** `.rollf`

**Arguments:** None

**Channels:** #tabletop, #bot_test

**Usable By:** Anyone