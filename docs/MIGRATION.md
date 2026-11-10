# Migration: haidaral/test to ra-email-fonts

Status: verified 2026-11-10, tag v1.0.0. All three new URLs were opened in a browser and
downloaded the font file. Response headers were not checked from the build environment.

Old URLs were read from the inline @font-face rules on https://www.radiantlyalive.com/
on 10 November 2026. Do not edit, move or delete anything in the old `haidaral/test` repo.
Emails already sent still load from it.

## URL mapping

| Klaviyo font name | Weight | Style | Old URL | New URL |
|---|---|---|---|---|
| `PPAgrandirText` | 400 | Normal | `https://raw.githubusercontent.com/haidaral/test/main/fonts/PPAgrandirText-Regular.woff2` | `https://cdn.jsdelivr.net/gh/radiantlyalive/ra-email-fonts@v1.0.0/fonts/PPAgrandirText-Regular.woff2` |
| `PPAgrandirGrande` | 400 | Normal | `https://raw.githubusercontent.com/haidaral/test/main/fonts/PPAgrandir-GrandRegular.woff2` | `https://cdn.jsdelivr.net/gh/radiantlyalive/ra-email-fonts@v1.0.0/fonts/PPAgrandir-GrandRegular.woff2` |
| `PPAgrandirGrandeHeavy` | 600 | Normal | `https://raw.githubusercontent.com/haidaral/test/main/fonts/PPAgrandir-GrandHeavy.woff2` | `https://cdn.jsdelivr.net/gh/radiantlyalive/ra-email-fonts@v1.0.0/fonts/PPAgrandir-GrandHeavy.woff2` |

## Steps in Klaviyo (done by a person, not by Claude)

1. Open the custom font entry with the name in the first column.
2. Replace the Source URL with the New URL from the same row. Leave the name, weight and
   style unchanged, so existing templates keep working.
3. Delete any empty variant row before saving.
4. Keep the fallback as Arial.
5. Save, then send a test to an Apple Mail or iPhone inbox and to Gmail.
   Apple should show Agrandir. Gmail should show Arial.

## Rollback

If a new URL fails in the test, paste the old URL from the same row back into Klaviyo.
