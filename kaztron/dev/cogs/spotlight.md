---
title: "Cogs: Spotlight"
last_updated: 26 February 2018
summary: "The Spotlight cog provides functionality which manages the World Spotlight community feature on the /r/worldbuilding Discord server."
---

The Spotlight cog provides functionality which manages the World Spotlight community feature on the /r/worldbuilding Discord server.

Two commands are public and can be used by all users. All other commands are mod-only, and are used to select, queue and announce spotlights.

## 1. spotlight

{% include tip.html content="For convenience, most sub-commands support a single-letter shorthand. Check each command's Usage section." %}

### 1.1. join

Join the Spotlight Audience. This allows users to be pinged by moderators or the Spotlight
Host for news about the spotlight (like the start of a new spotlight, or a newly released
schedule).

To leave the Spotlight Audience, use `.spotlight leave`.

**Usage:** `.spotlight join`

**Arguments:** None

**Channels:** Any

**Usable by:** Anyone


### 1.2. leave

Leave the Spotlight Audience.  See [1.1. join](#11-join) for more information.

To join the Spotlight Audience, use `.spotlight join` ([1.1](#11-join)).

**Usage:** `.spotlight leave`

**Arguments:** None

**Channels:** Any

**Usable by:** Anyone


### 1.3. list (shorthand: l)

List all the spotlight applications in summary form.

**Usage:**
* `.spotlight list`
* `.spotlight l`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


### 1.4. current (shorthand: c)

Show the currently selected application.

**Usage:**
* `.spotlight current`
* `.spotlight c`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


### 1.5. roll (shorthand: r)

Select a spotlight application at random, and set it as the currently selected application. Only applications that are marked 'ready for Spotlight' will be selected.

**Usage:**
* `.spotlight roll`
* `.spotlight r`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


### 1.6. select (shorthand: s)

Select a specific spotlight application, show it and set it as the currently selected application.

**Usage:**
* `.spotlight set <list_index>`
* `.spotlight s <list_index>`

**Arguments:**
* `<list_index>`: Required. The numerical index of a spotlight application, as shown with `.spotlight list` ([1.3](#13-list-shorthand-l)).

**Channels:** Any

**Usable by:** Moderators only

**Example:**
* `.spotlight set 5` - Set the currently selected application to entry #5, as shown in the list returned from `.spotlight list` ([1.3](#13-list-shorthand-l)).


### 1.7. showcase

Publicly announce the currently selected application in the Spotlight channel, and switch the Spotlight Host role to the application's owner (if valid).

**Usage:** `.spotlight showcase`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


### 1.8. queue (shorthand: q)

The `.spotlight queue` sub-command contains sub-sub-commands that let moderators manage a queue of upcoming spotlights.


#### 1.8.1 list (shorthand: l)

Lists the current queue of upcoming spotlights.

The queue is always ordered chronologically. If two queue items have the exact same date, the order between them is undefined.

**Usage:**
* `.spotlight queue list`
* `.spotlight q l`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


#### 1.8.2 add (shorthand: a)

Add a spotlight application scheduled for a given date.

You can either use the currently selected spotlight, or specify an index number for the spotlight application to add.

**Usage:**
* `.spotlight queue add <datespec> [list_index]`
* `.spotlight q a <datespec> [list_index]`

**Arguments:**
* `<datespec>`: Required, string. A string identifying the date. If the datespec contains spaces, quotation marks are *required*. The datespec can be:
    * An exact date: 2017-12-25, "25 December 2017", "December 25, 2017" (with quotation marks)
    * A time expression: "tomorrow", "next week", "in 5 days". Does **not** accept days of the week ("next Tuesday").
* `[list_index]`: Optional, int. The numerical index of a spotlight application, as shown with `.spotlight list` ([1.3](#13-list-shorthand-l)). If this is not provided, the currently selected application will be used (so you don't have to specify this argument if you're using `.spotlight roll`, `.spotlight select` or `.spotlight queue next`, for example).

{% include note.html content="KazTron will not take any action on the scheduled date. It is purely informational, intended for the bot operator, as well as determining the order of the queue." %}

{% include tip.html content="You can add the same Spotlight application to the queue multiple times (e.g. on different dates). To edit the date instead, use `.spotlight queue edit`." %}

**Channels:** Any

**Usable by:** Moderators only

**Examples:**
* `.spotlight queue add 2017-12-25` - Adds the currently selected application, scheduled on 25 December 2017.
* `.spotlight queue add "in 3 days" 13` - Adds application #13, scheduled


#### 1.8.2 edit (shorthand: e)

Change the scheduled date of a spotlight application in the queue.

{% include important.html content="This command takes a **queue index**, not a spotlight application number. Check the index with `.spotlight queue list`." %}

**Usage:**
* `.spotlight queue edit <queue_index> <datespec>`
* `.spotlight q e <queue_index> <datespec>`

**Arguments:**
* `<datespec>`: Required, string. A string identifying the date. This can be:
    * An exact date: 2017-12-25, "25 December 2017", "December 25, 2017" (with quotation marks)
    * A time expression: "tomorrow", "next week", "in 5 days". Does **not** accept days of the week ("next Tuesday").
* `[queue_index]`: Optional, int. The numerical position in the queue, as shown with `.spotlight queue list` ([1.8.1](#181-list-shorthand-l)).

{% include note.html content="KazTron will not take any action on the scheduled date. It is purely informational, intended for the bot operator, as well as determining the order of the queue." %}

**Channels:** Any

**Usable by:** Moderators only

**Examples:**
* `.spotlight queue edit 3 2017-12-31` - Changes the date of the 3rd queued application to 31 December 2017.


#### 1.8.3 next (shorthand: n)

Set the next spotlight in the queue as the currently selected spotlight, and remove it from the queue. This is useful when a new spotlight is ready to start, as you can then immediately use `.spotlight showcase` ([1.7](#17-showcase)) to announce it publicly.

**Usage:**
* `.spotlight queue next`
* `.spotlight q n`

**Arguments:** None

**Channels:** Any

**Usable by:** Moderators only


#### 1.8.4 rem (shorthand: r)

Remove a spotlight application from the queue.

If no queue index is passed, removes the last item in the queue.

{% include important.html content="This command removes by **queue index**, not by spotlight application number. Check the index with `.spotlight queue list`." %}

**Usage:**
* `.spotlight queue rem [queue_index]`
* `.spotlight q r [queue_index]`

**Arguments:**
* `[queue_index]`: Optional, int. The numerical position in the queue, as shown with `.spotlight queue list` ([1.8.1](#181-list-shorthand-l)). If this is not provided, the last queue item will be removed.

**Channels:** Any

**Usable by:** Moderators only

**Examples:**
* `.spotlight queue rem` - Remove the last spotlight in the queue.
* `.spotlight queue rem 3` - Remove the third spotlight in the queue.
