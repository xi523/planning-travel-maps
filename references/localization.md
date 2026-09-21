# Bilingual HTML / 双语旅行地图

## Output contract

Generate one HTML artifact with a visible 中文 / English language switch unless the user explicitly requests a single language. Default to the user's conversation language, allow switching without a network translation service, and preserve selected day, city, categories, map position and enabled layers. Persist language preference when local storage is available; storage failure must not break rendering.

Provide complete Chinese and English content: page title, dates and weekdays, itinerary, attractions, restaurant descriptions and recommended dishes, rating labels, booking states, transport legs, assumptions, warnings, image fallback, source labels, map legend, tooltips and accessibility labels. Set document.lang appropriately. Do not translate only the navigation chrome.

## Shared data

Keep IDs, coordinates, times, statuses, ratings and navigation targets shared. Use localized dictionaries for interface strings and localized fields for authored text, for example title: {zh: "...", en: "..."}. This is a conceptual shape, not a requirement to replace an existing compatible schema.

Retain the local official place name alongside translated names when useful for signs, drivers and navigation. External navigation queries should identify the actual business and branch, not rely on a literal translated name. Do not translate street names, citations or restaurant dishes into misleading invented official names.

Missing translations must be visible and tracked, not silently presented as a completed English version. Translate uncertainties faithfully: tentative must not become confirmed. Preserve local time zones, currencies and verification dates.

## Validation

Test language switching in overview, daily itinerary, route segments, food filters and an open popup. Verify that selected filters and route state remain unchanged, marker counts and destinations match, and all long content is translated. Check English wrapping on desktop and mobile, including long place names, scrollable popup bottoms and accessible labels.

Test with translation networks unavailable: embedded language content should still switch. A skill instruction is not proof that a particular generated HTML has passed these checks; report actual test coverage.
