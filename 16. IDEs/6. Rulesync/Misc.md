##### What is it

An open source package that  keeps your skills, subagents, etc. in sync across your different AI tools so that you don't have to keep doing the manual config steps for the same stuff across all of them. ([GH link](https://github.com/dyoshikawa/rulesync), [Reference](https://rulesync.dyoshikawa.com/reference/cli-commands.html))

The idea is that you put your skills, etc. in folder inside `.rulesync` and then run some rulesync commands that then copies them to appropriate folders for Claude Code, Windsurf, etc. 

##### Installation

Can be installed using Homebrew or npm.

```
brew install rulesync      # <---- If using Homebrew
npm install -g rulesync    # <---- If using npm
```

And then initialize it from project directory.

```
cd project-directory
rulesync init
```

That creates the following files in project directory.

```
.rulesync
├── commands
│   └── review-pr.md
├── hooks.json
├── mcp.json
├── rules
│   └── overview.md
├── skills
│   └── project-context
│       └── SKILL.md
└── subagents
    └── planner.md

rulesync.jsonc
```

##### Common commands

Creates the basic rulesync folder structure along with jsonc file

```
rulesync init
```

Do necessary config for the mentioned AI tools (`target` option) and featureset, i.e. skills, subagents, etc. (`features` option).

```
rulesync generate --targets "*" --features "*"
```

Download the skills, etc. from a given repo. The specific configuration is in the jsonc file.

```
rulesync fetch GH repo --features skills
```

Download only the skills, etc. mentioned in `sources` key.

```
rulesync install
```

##### rulesync.jsonc

A whole bunch of things that can be configured ([documentation](https://rulesync.dyoshikawa.com/guide/declarative-sources.html)).

Declarative skills are used when just specific skills should be downloaded (instead of all that happen in a `fetch`).

```
  "sources": [
     { "source": "owner/repo" },
     { "source": "org/repo", "skills": ["specific-skill"] },
  ],
```

> Will declarative sources also work for subagents, and rules?
