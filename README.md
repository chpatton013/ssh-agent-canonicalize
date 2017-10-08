# ssh-agent-canonicalize

A tool to help manage ssh-agent processes.

## Description

`ssh-agent-canonicalize` will create a single "canon" agent and kill all other
agent processes. It will then print the appropriate shell commands to configure
your environment for the canon agent. Repeated invocation of
`ssh-agent-canonicalize` will leave the canon agent running so you can save
yourself from hundreds of errant agents running all the time.

## Usage

Put `ssh-agent-canonicalize` on your PATH, then:

```
eval $(ssh-agent-canonicalize)
```

## Customization

The default canonical agent environment file location is
`/var/tmp/ssh-agent-canonicalize/env.source`.

This file path is controlled by two different environment variables:

* `SSH_AGENT_CANON_DEFAULT_ENV_DIR`
* `SSH_AGENT_CANON_DEFAULT_ENV_BASE`

You can change these variables to control where the environment file is stored.
