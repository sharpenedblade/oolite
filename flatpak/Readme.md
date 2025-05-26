## Building

Install flatpak-builder

```bash
flatpak install --user org.flatpak.Builder
```

Run the build. Change `$ID` to something else if you want seperate save and AddOn dirs for testing.

```bash
ID="space.oolite.oolite"
flatpak run org.flatpak.Builder \
  --user \
  --force-clean \
  --subject="$(git show --format=%s -s)" \
  --body="$(git show --format=%b -s)" \
  --collection-id="$ID" \
  --repo=repo \
  builddir \
  space.oolite.oolite.yml
```

Install the package and the debuginfo files:
```
flatpak install --user --reinstall "$PWD/repo" "$ID" "$ID".Debug
```

## Clearing the build cache

If you experience compile errors or crashes, run `rm -r .flatpak-builder`, then follow the build instructions again.
