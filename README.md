# Install Obsidian in GitHub Actions

Installs Obsidian for use with E2E tests or similar. 

## Compatibility notes

* Crapple shitOS: Not supported
* Windows: Supported, but flaky due to problems with the installer. There's a timeout set for 2 minutes on the install step to prevent this from going on for too long.
* Linux (Ubuntu): Supported, works reliably

Note that both Linux and Windows can be flaky due to GitHub itself being flaky. No caching is implemented at the time of writing, and retrieval errors from GitHub does happen on occasion. 

## Usage
```yaml
- name: Install Obsidian
  uses: LunarWatcher/install-obsidian@master
  with:
    # Whether or not to grab the latest version. Mutually exclusive with `version`
    latest: true
    # Used to specify which version to download. Mutually exclusive with `latest`. 
    # The version MUST correspond to a tag in the obsidian release repo:
    # https://github.com/obsidianmd/obsidian-releases/releases
    version: ''
```

### Outputs
* `path`: The path to the obsidian executable. This is purely meant as a convenience tool, as the paths are secretly hard-coded
* `version`: The version of obsidian that was downloaded. If `version` is specified as an input, this field will be identical.
