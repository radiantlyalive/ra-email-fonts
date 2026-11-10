# CLAUDE.md

Project: ra-email-fonts. Font host for Radiantly Alive Klaviyo emails. Read README.md first.

## Rules

- Never edit, convert, subset or rename a font file. Copy only.
- Family names in CSS must match Klaviyo exactly: `PPAgrandirText`, `PPAgrandirGrande`,
  `PPAgrandirGrandeHeavy`.
- Never use `raw.githubusercontent.com` in a URL you write. Use tagged jsDelivr or Pages.
- Never delete or overwrite a published tag or file. New change means new tag.
- Do not touch Klaviyo. Output URL mappings for a human to paste.
- Do not touch or delete the old `haidaral/test` repo.
- Stop before the first `git push` and wait for confirmation of repo visibility and licence.
- No em dashes in any file. No emojis.
- Commit messages: short, imperative, one line.

## Verify a font file

```bash
head -c4 file.woff2            # must print wOF2
pip install fonttools brotli --break-system-packages
python3 -I -c "from fontTools.ttLib import TTFont; f=TTFont('file.woff2'); print(f['name'].getDebugName(4), len(f.getGlyphOrder()))"
```

## Verify a published URL

```bash
curl -sIL URL | grep -iE '^(HTTP|content-type|content-length|access-control-allow-origin)'
```

Expect 200, a font or octet-stream content type, and `access-control-allow-origin: *`.
