---
title: "Cogs: ModNotes"
last_updated: 21 February 2018
summary: "The ModNotes cog implements the storage of records for use by moderators in the course of their duty."
---

{% include important.html content="This document is a draft specification for features on the v2.0 roadmap. It is a living document and subject to change." %}

The **ModNotes** cog implements the storage of records for use by moderators in the course of their duty, and as a tool of communication between moderators. It allows arbitrary text records to be recorded, alongside with the author and timestamp, associated to various community users.

## 1. notes

Access moderation records by user.

10 notes are shown per page. This limitation is partially to limit the number of messages needed to show one page (typically 2 messages now) due to Discord message size limits. This, in turn, prevents it from hitting a rate limit too easily. It is unlikely to be increased.

**Usage:**
* `.notes <user> [page]`

**Arguments:**
* `<user>`: Required. The user for whom to find moderation notes. This can be an `@mention`, a Discord ID (numerical only), or a KazTron ID (starts with `*`).
* `[page]`: Optional. The page number to access, if there are more than 1 pages of notes. Default: 1.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes @User#1234`
* `.notes @User#1234 3`


### 1.1. add (shorthand: a)

Add a new note.

If the `<user>` is not already known in the database, an entry will be created, using their current nickname as the canonical name. There is no need to create the user in advance.

**Usage:**
* `.notes add <user> <type> [OPTIONS] <note_contents>`
* `.notes a <user> <type> [OPTIONS] <note_contents>`

**Arguments:**
* `<user>`: Required. The user to whom the note applies. See [Section 1](#1-notes).
* `<type>`: Required. The type of record. One of:
  * `note`: Generic note not falling under other categories.
  * `good`: Noteworthy positive contributions to the community.
  * `watch`: Moderation problems to watch out for.
  * `int`: Moderator intervention events.
  * `warn`: Formal warning issued.
  * `temp`: Temporary ban issued.
  * `perma`: Permanent ban issued.
  * `appeal`: Formal appeal received.
* `[OPTIONS]`: Optional. Options of the form:
  * `timestamp="timespec"`: Sets the note's time (e.g. the time at which a note happened). Default is "now". Instead of `timestamp`, you can also use the synonyms `starts`, `start` or `time`.
  * `expires="timespec"`: Sets when a note expires. This is purely documentation: for example, to take note of when a temp ban ends, or a permaban appeal is available, etc. Default is no expiration. Instead of `expires`, you can also use the synonyms `expire`, `ends` or `end`.
  * The timespec is "smart". You can type a date and time (like "3 Dec 2017 5PM"), or relative times in natural language ("10 minutes ago", "in 2 days", "now"). Just make sure not to forget quotation marks.
* `<note_contents>`: The remainder of the command message is stored as the note text.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes add @BlitheringIdiot#1234 perma Repeated plagiarism.` - This creates a record timestamped for right now, with no expiry date.
* `.notes add @BlitheringIdiot#1234 temp expires="in 7 days" Insulting users, altercation with intervening mod.` - This creates a record timestamped for right now, that expires in 7 days.
* `.notes add @CalmPerson#4187 good timestamp="2 hours ago" Cool-headed, helped keep the BlitheringIdiot plagiarism situation from exploding` - This creates a record for an event 2 hours ago.
* `.notes a @BlitheringIdiot#1234 temp Drive-by advertising` - Uses the `a` shorthand for this command.


### 1.2. rem (shorthand: r; alias: remove)

Remove an existing note.

To prevent accidental data deletion, the removed note can be viewed and restored by admin users.

**Usage:**
* `.notes rem <note_id>`
* `.notes r <note_id>`

**Arguments:**
* `<note_id>`: Required. The ID of the note to remove. See [Section 1](#1-notes) for how to list notes and IDs.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes rem 122` - Removes note ID 122.
* `.notes r 124` - Removes note ID 124. Uses the `r` shorthand command.


### 1.3. removed

Show all removed notes, optionally filtered by a user.

**Usage:**
* `.notes removed <user> [page]`

**Arguments:**
* `<user>`: Required. The user to filter by, or `all`. See [Section 1](#1-notes).
* * page: Optional[int]. The page number to access, if there are more than 1 pages of notes. Default: 1.

**Channels:** Admin channels

**Usable by:** Administrators only


### 1.3. restore

Restore a removed note.

**Usage:**
* `.notes restore <note_id>`

**Arguments:**
* `<note_id>`: Required. The ID of a previously removed note to restore. Use `.notes removed` to list removed notes.

**Channels:** Mod and bot channels

**Usable by:** Administrators only


### 1.4. purge

Permanently destroy a removed note.

**Usage:**
* `.notes purge <note_id>`

**Arguments:**
* `<note_id>`: Required. The ID of a previously removed note to purge. Use `.notes removed` to list removed notes.

**Channels:** Mod and bot channels

**Usable by:** Administrators only


### 1.5. finduser

User search.

This command searches the name and aliases fields. 20 results are shown per page.

**Usage:**
* `.notes finduser <search_term> [page]`

**Arguments:**
* `<search_term>`: Required. A substring to search for in the user database's name and aliases fields.
* `[page]`: Optional. The page to show, if multiple pages of results. Default: 1.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes finduser Indium` - This command could, for example, match a user called "IndiumPhosphide".


### 1.6. name

Set the canonical name by which a user is known. This replaces the previous name; to add aliases, see [Section 1.4](#14-alias).

**Usage:**
* `.notes name <user> <new_name>`

**Arguments:**
* `<user>`: Required. The user to whom the note applies. See [Section 1](#1-notes).
* `<new_name>`: Required. The new canonical name to set for a user. Max 32 characters, no newlines.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes name @FireAlchemist#1234 Roy Mustang`


### 1.7. alias

Set or remove alternative names a user is known under.

Suggested usage: `/u/RedditUsername` for Reddit usernames, `R:Nickname` for IRC registered nicknames, `nick!username@hostname` masks for unregistered IRC users (or whatever format you prefer to communicate the relevant information, this is freeform).

**Usage:**
* `.notes alias <add|rem> <user> <alias>`

**Arguments:**
* `<add|rem>`: Required. Whether to add or remove the indicated alias.
* `<user>`: Required. The user to whom the note applies. See [Section 1](#1-notes).
* `<alias>`: Required. The alias to set for the user. Max 32 characters, no newlines.

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes alias add @FireAlchemist#1234 The Flame Alchemist`


### 1.8. group

Group and ungroup users together.

An identity group identifies users which are all considered to be the same
individual. The .notes command will show the user info and records for both simultaneously,
if one of them is looked up. The users remain separate and can be removed from the group
later.

#### 1.8.1. group add (shorthand: group a)

Group users together.
        
If one user is not in a group, that user is added to the other user's group. If both users are in separate groups, both groups are merged. This is irreversible.

See [1.8 group](#18-group) for more information on grouping.

**Usage:**
* `.notes group add <user1> <user2>`

**Arguments:**
* `<user1>` and `<user2>`: Required. The two users to group together. See [Section 1](#1-notes).

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes group add @FireAlchemist#1234 @TinyMiniskirtEnthusiast#4444`


#### 1.8.2. group rem (shorthand: group r; alias: group remove)

Remove a user from the group.

See [1.8 group](#18-group) for more information on grouping.

**Usage:**
* `.notes group rem <user>`

**Arguments:**
* `<user>`: Required. The user to unlink. See [Section 1](#1-notes).

**Channels:** Mod and bot channels

**Usable by:** Moderators only

**Example:**
* `.notes group rem @FireAlchemist#1234`