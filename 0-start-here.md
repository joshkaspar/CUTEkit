1. Customize (optional)

Open 1-config.yaml. Tools are grouped by type -- uncomment anything you
want to add, comment out anything you don't need.

2. Generate

Requires python3-yaml: apt install python3-yaml

	 python3 cutekit.py generate

3. Run setup

Run as root. Takes a few minutes. It creates a non-root sudo user for
you (you'll be prompted for a username and password) and copies root's
SSH key over so you can log in as that user afterward.

       sudo bash 3-setup.sh

4. Finish up

Open 4-post-install-steps.md -- a short checklist to get the
environment running.
