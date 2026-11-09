# CUTEkit runs on the server

CUTEkit is run on the server being set up, which is why the server needs
Python 3 and `python3-yaml`. Two alternatives were considered and dropped:
generating a setup script in GitHub Actions (abandoned in e4354d7), and
generating it on a separate authoring machine then copying it over (made
unsupported in 4818d54). The original reasons weren't recorded. Today's
reason: running on the server keeps it to one machine and one clone, with
nothing to sync, and lets the user edit `1-config.yaml` and rerun on the spot.
