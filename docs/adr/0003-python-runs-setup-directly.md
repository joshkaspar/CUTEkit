# Python runs setup directly; no generated shell script

CUTEkit is one Python program that reads `1-config.yaml` and performs the
install itself, echoing each command as it runs. It no longer generates
`3-setup.sh` or `99-lock-doors.sh`. The shell script was left over from the
original all-bash version of the project and from the two-machine workflow
(see ADR-0002). Once both were gone it saved no steps, and producing bash
from Python meant layers of nested quoting that were hard to read and
maintain. The script's one real benefit, being able to review every command
before it runs as root, is kept by a `plan` subcommand that prints what
`install` would do without doing it.

## Considered Options

- Keep generating a shell script: reviewable, and the generator never needs
  root, but it keeps the Python-writes-bash layer
- A static bash script that reads the YAML: bash can't parse YAML without
  adding a tool like `yq`
- Python runs setup directly (chosen)

## Consequences

- The program runs as root for `install` and `update`. `plan` needs no root.
- Shell snippets from the config (`custom_setup`, `installed_check`) still
  run through bash, but are handed over exactly as written, one layer deep.
- Docs (`2-post-install-steps.md`, `tool-reference.md`) are still generated.
- `install` copies the program to `/usr/local/bin/cutekit` and the config to
  `/etc/cutekit/config.yaml`, so the clone can be deleted afterwards. Running
  `cutekit install` with no config path reapplies that copy.
- The installed program uses `#!/usr/bin/python3` (Ubuntu's Python, which
  has `python3-yaml`), never `env python3`, which could resolve to a
  mise-managed Python without it.
