# homebrew-tap

Homebrew tap for [Skillcaddy](https://github.com/chenweil/skillcaddy).

```bash
brew tap chenweil/tap
brew install chenweil/tap/skillcaddy
```

The formula installs the published npm tarball, so the Homebrew version and
the npm version always match. Skillcaddy keeps the central skill library in
`~/.skillcaddy/library`, outside the Cellar — upgrading or reinstalling the
formula never touches your library.

## How this tap is maintained

`Formula/skillcaddy.rb` is a copy of the formula kept in the main repository
(`Formula/skillcaddy.rb` there). After every npm release, the main repository
runs:

```bash
bash scripts/update-homebrew-formula.sh   # refresh version + sha256
bash scripts/publish-homebrew-tap.sh      # copy into this tap and push
```

The checksum is computed from the tarball on the npm registry and
cross-checked against the registry's own `dist.shasum`, so a formula here
always points at bytes that npm actually serves.
