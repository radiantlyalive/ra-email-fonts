# ra-email-fonts

Stable host for the Radiantly Alive brand fonts used in Klaviyo emails.

Replaces `raw.githubusercontent.com/haidaral/test/main/fonts/`, which is a personal
test repo with no CDN behind it.

## Repo layout

```
ra-email-fonts/
  README.md
  CLAUDE.md
  .gitattributes
  fonts/
    PPAgrandirText-Regular.woff2
    PPAgrandir-GrandRegular.woff2
    PPAgrandir-GrandHeavy.woff2
  css/
    ra-fonts.css
  docs/
    MIGRATION.md
```

## Font files

Family names must stay identical to the custom font entries in Klaviyo. Do not rename.

| File | CSS family | Weight |
|---|---|---|
| `PPAgrandirText-Regular.woff2` | `PPAgrandirText` | 400 |
| `PPAgrandir-GrandRegular.woff2` | `PPAgrandirGrande` | 400 |
| `PPAgrandir-GrandHeavy.woff2` | `PPAgrandirGrandeHeavy` | 600 |

Only a 400 weight exists for `PPAgrandirText`. Bold text in email gets faux bold in clients
that load the font. Add a real bold file here only if the licence includes one.

## Hosting

Use a tagged jsDelivr URL. The tag makes the URL immutable.

```
https://cdn.jsdelivr.net/gh/<owner>/ra-email-fonts@v1.0.0/fonts/PPAgrandirText-Regular.woff2
```

GitHub Pages is the alternative:

```
https://<owner>.github.io/ra-email-fonts/fonts/PPAgrandirText-Regular.woff2
```

Rules:

- Never use `raw.githubusercontent.com` in a new setup. It caches for 5 minutes, has no
  CDN and can rate limit.
- Never move, rename or overwrite a published file. Publish a new tag instead.
- Never delete an old tag. Emails already sent still point at it.
- jsDelivr only serves public repos. A private repo needs Pages (paid plan) or another host.

## Using it in Klaviyo

Klaviyo takes one URL per font face. `css/ra-fonts.css` is a reference copy, not what Klaviyo
loads. After a release, replace each face URL in the Klaviyo custom font entry with the new
one. `docs/MIGRATION.md` lists the old and new URL for each face.

Email stack, set inline on every text element:

```
PPAgrandirText, Arial, 'Helvetica Neue', Helvetica, sans-serif
```

## What to expect in inboxes

| Client | Brand font loads? |
|---|---|
| Apple Mail, iPhone Mail | yes |
| Gmail (web and app) | no, shows Arial |
| Outlook desktop | no, shows Arial |
| Yahoo, most Android mail apps | no, shows Arial |

Arial in Gmail and Outlook is the fallback working as designed. Hosting cannot change it.
Anything brand critical, such as a wordmark, belongs in an image with alt text.

## Licence

The font files are not covered by any licence of this repo. The Agrandir licence terms
(the Email & Funnels docs note web and print, not email) must be confirmed by Rafa before the
files are made public. If the answer is no, host them privately and skip jsDelivr.
