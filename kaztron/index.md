---
title: "KazTron - Introduction"
---

KazTron is the /r/worldbuilding Discord server's resident helper bot! It mostly helps the moderators manage the community and run features like the World Spotlight, with a few automation features that happen behind the scenes, and a few commands of use to our members.

This website documents the usage of the various commands, organised by module. Note that not all modules may be loaded, depending on needs as judged by the moderation team.

{% include note.html content="Setting up and running your own instance of KazTron is outside the scope of this manual. For any inquiries, you can get in touch with us via Reddit modmail (click the Feedback link above) or the #meta channel of our Discord server." %}

{% include important.html content="KazTron is designed for use on only one Discord server at a time. It is not possible to invite it to other servers. To get KazTron, you would need to host it yourself on a separate bot account." %}

## How to use KazTron commands

KazTron is always monitoring all text channels for commands. The structure of a command is as follows:

```
<prefix><command_name> [arg1 [arg2 [arg3...]]]
```

The prefix, in this case `.`, is how KazTron identifies a command intended for it, versus any normal message. This is followed by the command name, a space, and then any number of arguments separated by spaces (very similarly to command line tools, IRC bots, and IRC NickServ/ChanServ commands). If an argument contains spaces, you should enclose it in quotes to ensure it gets interpreted as a single argument.

{% include note.html content="Some commands are restricted based on user account and text channel. For example, some commands are moderator-only, others can only be used on specific channels." %}

{% include tip.html content="If you use a command KazTron does not know, it will PM you to let you know." %}

{% include tip.html content="In order to avoid spamming channels, some commands will cause KazTron to delete the message containing your command and PM you to confirm the action. If you see your command message instantly disappear, don't panic&mdash;check your PMs!" %}

### Examples

If you want to be notified about World Spotlight events and updates, you can type this command *in any channel*:

```
.spotlight join
```

If you want to roll dice, say three 20-sided dice, you could type the following message in the #tabletop channel (this is a channel-restricted command):

```
.roll 3d20
```

## Getting Help

In addition to this manual, you can always get contextual help from within Discord. To get a list of commands you can use, type `.help` into any channel on the server. To get help on specific commands, you can type `.help <command>`, or even get help with subcommands using `.help <command> <subcommand>`.

For example, `.help spotlight` will give you general information on the spotlight bot features, whereas `.help spotlight join` will specifically tell you about the "join" subcommand and its syntax. (In this case, the commands are both very simple, though!)

{% include note.html content="Help files are contextual: KazTron will only list commands that you're allowed to use in the channel where you asked for help. So you won't see `.roll` unless you ask for `.help` in #tabletop, and you won't see mod-only commands unless you're a moderator." %}

## The Team

KazTron is developed and operated by:

<div class="row">
    {% for author in site.data.kaztron.authors %}
    <div class="col-md-4 col-sm-6">
        <div class="panel panel-default text-center">
            <div class="panel-heading">
                <!-- TODO: user icons -->
                <span class="fa-stack fa-5x">
                      <i class="fas fa-circle fa-stack-2x text-primary"></i>
                      <i class="fas fa-user fa-stack-1x fa-inverse"></i>
                </span>
            </div>
            <div class="panel-body">
                <h4>{{ author.name }}</h4>
                <p>{{ author.role }}</p>
                {% if author.github != null %}
                <div><a href="https://github.com/{{ author.github | downcase }}"><i class="fab fa-github"></i> {{author.github}}</a></div>
                {% endif %}
                {% if author.reddit != null %}
                <div><a href="https://reddit.com/u/{{ author.github | downcase }}"><i class="fab fa-reddit-alien"></i> /u/{{author.reddit}}</a></div>
                {% endif %}
                {% if author.discord != null %}
                <div><i class="fab fa-discord"></i> {{author.discord}}</div>
                {% endif %}
            </div>
         </div>
    </div>
    {% endfor %}
</div>

{% include links.html %}
