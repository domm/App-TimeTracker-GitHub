# NAME

App::TimeTracker::Command::GitHub - App::TimeTracker GitHub plugin

# VERSION

version 1.000

# DESCRIPTION

Connect tracker with [GitHub](https://github.com/).

Using the GitHub plugin, tracker can fetch the name of an issue and use
it as the task's description; generate a nicely named `git` branch
(if you're also using the `Git` plugin).

# CONFIGURATION

## plugins

Add `GitHub` to the list of plugins.

## github

add a hash named `github`, containing the following keys:

### user \[REQUIRED\]

Your github user name. Best stored in your global TimeTracker config file.

### token \[REQUIRED\]

Your personal access token. Get it from your github settings
(Developer Settings, Personal access token): https://github.com/settings/tokens

Best stored in your global TimeTracker config file.

### repo \[REQUIRED\]

The name of the repository you are working on. Currently a required
entry to the config file, but we might upgrade it to a command line
param and/or try to guess it from the current working dir or your git
config.

### api\_uri

Optional.

Set this to the URL of your local GitHub Enterprise installation.

# NEW COMMANDS

No new commands

# CHANGES TO OTHER COMMANDS

## start, continue

### --issue

    ~/perl/Your-Project$ tracker start --issue 42

If `--issue` is set and we can find an issue with this id in your current repo

- set or append the issue name in the task description ("Rev up FluxCompensator!!")
- add the issue id to the tasks tags ("issue#42")
- if `Git` is also used, determine a save branch name from the issue name, and change into this branch ("42-rev-up-fluxcompensator")
- TODO: assign to your user, if `set_assignee` is set and issue is not assigned
- TODO: reopen a closed issue if `reopen` is set
- TODO: modifiy the labels by adding all labels listed in `labels_on_start.add` and removing all lables listed in `labels_on_start.add`

# AUTHOR

Thomas Klausner <domm@plix.at>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2020 by Thomas Klausner.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
