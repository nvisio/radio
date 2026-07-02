# radio.nvis.io — Oh My Radio deep-link host

Satellite GitHub Pages site for the **Oh My Radio** iOS app
([hkmoon/kbsCong](https://github.com/hkmoon/kbsCong)). It exists because
GitHub Pages allows one custom domain per repo — the main site
([nvisio/kradio](https://github.com/nvisio/kradio) → kradio.nvis.io) keeps the
catalogue, legal pages, and featured/health JSON; this repo serves only the
Universal-Link surface on the shorter domain:

| Path | Purpose |
|---|---|
| `/.well-known/apple-app-site-association` | AASA for `applinks:radio.nvis.io` (app ID `JD6369T7Y6.com.hkmoon.kbsradio`, `/play*` only). Must serve HTTP 200 with **no redirect** — never move or rewrite it. |
| `/play?name=…&url=…` | Shared-station landing page: og tags for link previews, Smart App Banner, and a `kradio://play?…` custom-scheme fallback for devices without the Universal Link association (older app versions / app not installed). |
| `/og-icon.png` | Link-preview image referenced by `play.html`. |
| `/assets/track.js` | Click beacon (radio-clicks.nvisio.workers.dev), copied from the main site. |

`.nojekyll` keeps GitHub Pages from running Jekyll, so the dot-folder
`.well-known` is published as-is. `CNAME` binds the custom domain.

The app accepts both hosts (`kradio.nvis.io` stays valid for links already
shared); new share links are generated with `radio.nvis.io`.
