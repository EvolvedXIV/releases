# releases

The central plugin repository Dalamud reads for every EvolveXIV plugin for FINAL FANTASY XIV.

## Installing EvolveXIV plugins

1. In game, open `/xlsettings` → **Experimental** → **Custom Plugin Repositories**.
2. Add this URL, tick *Enabled*, and save:

   ```
   https://raw.githubusercontent.com/EvolveXIV/releases/main/repo.json
   ```

3. Open `/xlplugins` and install any of the plugins below. New EvolveXIV plugins appear there automatically.

| Plugin | Repository |
|---|---|
| Party Icons Evolved | [EvolveXIV/party-icons-evolved](https://github.com/EvolveXIV/party-icons-evolved) |

## How repo.json is maintained

`repo.json` lists one entry per plugin. The plugin zips are attached to GitHub releases in each plugin's own
repository; this file only points at them.

Entries are not edited by hand. Each plugin repository has a **Release** workflow that publishes a release and
then updates **only its own entry** here (adding it on the first release), using `scripts/make_repo_json.py`
from that plugin repository. Text such as the punchline or description comes from the plugin's manifest, so
change it there; a hand edit here is overwritten by the next release.

To add a new plugin, follow "Adding a new plugin to the central repository" in the `dalamud-plugin` skill in
[EvolveXIV/dalamud_reference](https://github.com/EvolveXIV/dalamud_reference). In short: copy its templates into
the new plugin repository and give that repository a `RELEASES_TOKEN` secret (a token with
*Contents: Read and write* on this repository).

This repository must stay public: Dalamud downloads `repo.json` without logging in.
