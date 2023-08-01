# ssh-agent-canonicalize

A tool to help manage `ssh-agent` processes.

## Description

`ssh-agent-canonicalize` will create a single "canon" agent and kill all other
agent processes. It will then print the appropriate shell commands to configure
your environment for the canon agent, and invoke `ssh-add` if your agent process
is currently empty.

Repeated invocation of `ssh-agent-canonicalize` will leave the canon agent
running so you can save yourself from hundreds of errant agents running all the
time.

## Usage

Put `ssh-agent-canonicalize` on your PATH, then:

```
eval $(ssh-agent-canonicalize)
```

## Customization

The canonical agent environment file location is
`$XDG_RUNTIME_DIR/ssh-agent-canonicalize/env.source`. If `$XDG_RUNTIME_DIR` is
not set, then `/tmp/user/$(id -u)/ssh-agent-canonicalize/env.source` is used
instead.

`ssh-add` will attempt to add the default `~/.ssh/id_*` keyfiles when invoked
with no arguments. If you want to use specific keyfiles, add them to
`~/.ssh/.ssh-agent-default-keys` (one relative filepath per line).

## License

Licensed under either of

* Apache License, Version 2.0 (LICENSE-APACHE or http://www.apache.org/licenses/LICENSE-2.0)
* MIT license (LICENSE-MIT or http://opensource.org/licenses/MIT) at your option.

### Contribution

Unless you explicitly state otherwise, any contribution intentionally submitted
for inclusion in the work by you, as defined in the Apache-2.0 license, shall be
dual licensed as above, without any additional terms or conditions.
