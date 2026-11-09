# CUTEkit never writes the user's config files

CUTEkit puts all of its shell and tool configuration in system-level locations
(`/etc/zsh/zshenv`, `/etc/zsh/zshrc`, `/etc/mise/config.toml`) and never creates
or overwrites files the user owns, such as `~/.zshrc`, `~/.zprofile` or
`~/.config/mise/config.toml`. Earlier versions overwrote `~/.zshrc` and
`~/.zprofile`, which suppressed the zsh first-run wizard, clobbered existing
setups, and clashed with dotfile managers like chezmoi. Keeping CUTEkit's
defaults in `/etc` lets the user's own files layer on top and stay theirs.

## Consequences

- Allowed exceptions: creating the home directory for a new user, writing
  `~/.ssh/authorized_keys` when copying root's key, and data that tools write
  for themselves (e.g. mise installing into `~/.local/share/mise`).
- Coding-agent instructions are delivered via `post_install` notes, not by
  writing agent config files in `~/`.
