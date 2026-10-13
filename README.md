# Optimizing TikTok Events API in GTM Server-Side with Enhanced Consent and Data Handling

You can use this tag in the Google Tag Manager Server-Side container to configure the TikTok Events API and manage cookies, data transmission, and identifiers with built-in consent controls.

The tag operates based on GA4 requests and supports custom settings and parameters. It is based on the [official TikTok Events API template](https://github.com/tiktok/gtm-template-eapi) published by TikTok, extended by Sirdata to be GDPR Ready and to improve Event Match Quality (additional advanced matching fields such as name, city, zip code and country).

The TikTok Events API serves the same purpose as the TikTok Pixel, tracking user interactions on your website. However, while the Pixel processes requests in the user's browser, the Events API operates through a cloud server, enabling various optimizations such as bypassing ad blockers.

This tag works with any container hosting service (Google Cloud, Sirdata, and others), and is optimized for Sirdata's data enrichment layer, which is compatible with all hosting platforms. This additional layer of data enables several enhancements, including:
- Utilizing TCF consent signals in addition to Consent Mode signals
- Supporting a cookieless user ID when consent is not provided
- Handling consent under GDPR where applicable, and adjusting behavior where GDPR does not apply.

## GDPR Ready behavior

- Consent is detected automatically from Google Consent Mode (`gcs`), from the TCF consent signals forwarded by Sirdata's GTM Helper layer (`Gtm-Helper-Consent-Personalized-Ads`), and from GDPR applicability (`Gtm-Helper-Gdpr-Applies`).
- The `ttclid` and `_ttp` cookies are only read and written when consent is given.
- Personal data (email, phone, name, address, stored user agent) is only forwarded when consent is given.
- An experimental mode allows sending Events API data without consent using Sirdata's site-only cookieless user ID (no cookie is read or written, and no personal data is forwarded).

## Matching your TikTok catalog

When the GA4 `item_id` differs from the SKU ID of your TikTok catalog, enable **Rewrite content_id** (Properties section, GA4 e-commerce data) to align them: add a prefix and replace characters. For example, `437-1604` with prefix `FR` and `-` replaced by `v` becomes `FR437v1604`.

👉 For [Sirdata](https://sgtm.sirdata.io/login) clients, **many additional automatic optimizations are available**, such as integrated third-party ID management, enhanced consent handling, and advanced data enrichment. These features significantly improve TikTok's Event Match Quality score, boosting campaign efficiency and tracking precision.
