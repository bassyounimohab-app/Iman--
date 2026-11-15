# آيات ومعانٍ — Quranic Concepts

A bilingual, mobile-first progressive-web-app prototype for exploring Quranic themes.

## Run

Serve this directory from a local web server (for example `python -m http.server 8000`) and open `http://localhost:8000`. The UI works as a static site; Arabic ayah text and Pickthall English translation are fetched when a verse is opened, so an internet connection is required for verse text. The concept index itself is local.

On a phone, open the hosted page in Safari/Chrome and use **Add to Home Screen** to install it as a PWA-style app. This is a web app prototype, not a signed App Store / Google Play binary.

## Data model

`concepts.json` contains bilingual concept records with `direct` and `thematic` reference arrays. A reference may be a single ayah (`2:153`) or a range (`96:1-5`). Current UI loads individual references; ranges are shown as references but need range expansion before release.

## Important editorial limitation

This is a starter thematic index, not an exhaustive or scholarly-certified concordance. The boundary of a concept is interpretive: direct references and broader thematic connections must be checked against the full Quran and reliable tafsir by qualified reviewers. Do not market the current list as “all ayat.” The database deliberately labels its two relevance levels and includes a review status.

## Quran text attribution

Arabic Uthmani text is retrieved at runtime from AlQuran Cloud's Quran API (`api.alquran.cloud`, edition `quran-uthmani`). English is retrieved using the Pickthall edition (`en.pickthall`). Verify the API's current terms and the translation edition's reuse conditions before production redistribution. The app does not bundle either text.

For an alternative licensed Arabic source, Tanzil's text terms require verbatim use, attribution, and a link to Tanzil: https://tanzil.net/docs/text_license. Do not alter the Quranic Arabic text.

## Production roadmap

1. Expand ranges into individual ayah IDs and validate all IDs against the canonical 6,236-ayah corpus.
2. Build a full-coverage candidate retrieval pipeline using Arabic roots, lemmas, translations, and tafsir; do not rely on keyword search alone.
3. Have qualified Arabic/Quran reviewers classify every candidate as direct, contextual, or weak/related, with tafsir citations and reviewer/version metadata.
4. Add more licensed translations, audio, offline caching, accessibility, bookmarks, and tests.
5. Add a formal editorial policy for differences of interpretation and concept boundaries.

## License

Original app code and the initial concept taxonomy are provided for reuse. External Quran text and translation rights remain with their respective sources.

The service worker caches the app shell and concept database after first load. Verse text remains online-only in this prototype.
