# Travel Planning & Interactive Maps

[中文说明](README.md)

A reusable Codex skill that turns a destination, a text itinerary, or booking screenshots into a practical travel plan and an interactive HTML map.

## Real Demo Screenshots

These full desktop screenshots show an existing Penang and Phuket itinerary, including date and city switches, attractions, transport and descriptions. The example schedule is not a fixed template for other travelers. Ratings are historical verification snapshots, not live data. This demo is Chinese-only: bilingual output is required by the updated skill but has not been implemented or verified in this particular demo.

### 1. Multi-day overview

Switch dates and cities at the top, scan daily plans on the left, and locate attractions and transport points on the map.

![Multi-day Penang overview](docs/images/trip-overview.png)

### 2. Daily transport and routes

See the day's schedule, walking and taxi estimates, segment navigation and route markers together. Dashed lines indicate visit order, not actual road geometry.

![Daily schedule and transport](docs/images/trip-transport.png)

### 3. Attraction details

Scroll the side panel for highlights, suggested visit durations and practical notes while keeping the day's map visible.

![Attraction descriptions alongside the map](docs/images/trip-attractions.png)

### 4. Another city

Switching to Phuket updates dates, plans and map locations together.

![Phuket city view](docs/images/trip-phuket.png)

### 5. Food details

| Category filtering | Ratings, photos and scrollable details |
| --- | --- |
| ![Coffee shop category filter](docs/images/food-filter.png) | ![Restaurant rating and scrollable map popup](docs/images/food-popup.png) |

Food candidates start hidden. Enable the food layer and filter by categories such as cafes, desserts or late-night food. Open a marker for ratings, review counts, verification dates and real photos; scroll within the popup to reach descriptions and navigation. Other attraction layers can remain visible for context.

Basemap © OpenStreetMap contributors; map UI uses Leaflet. Business photos shown in the interface come from Google Maps business pages and belong to their respective owners. This repository includes screenshots, not a personal itinerary HTML or a hosted live demo.

## Capabilities at a Glance

| Stage | Input | Expected output |
| --- | --- | --- |
| Start from scratch | A destination, optional duration and interests | Neighborhood overview, attractions, suggested trip lengths and alternative plans |
| Work around bookings | Text or screenshots; one-way or return flights; partial hotel bookings | Confirmed facts, unknowns, fixed appointments and time-zone constraints |
| Attractions and photography | Interests, heat tolerance, pace and photo preferences | Nearby combinations, visit durations, photo stops, transport and fallback plans |
| Choose food | Categories or accessible saved recommendations | Categorized candidates, rating evidence, dishes, priorities and route compatibility |
| Build a map | Selected plan or explicitly requested draft | Overview, daily and segment views, popups, optional layers and external navigation |
| Revise | Changed hotels, appointments or attractions | Consistent updates while preserving unaffected decisions |
| Share | Explicit publishing request | Privacy review, authorized deployment and version/link verification |

Typical deliverables: trip.json (shared data), itinerary.md (readable plan), trip-map.html (interactive map), and an optional food guide. Without routing data, route lines show visit order rather than turn-by-turn directions.

The screenshots demonstrate implemented food filtering, markers, rating/photo display and scrollable popups. Broader planning and bilingual requirements guide future generation and require per-artifact verification. This is not an automatic booking service, a live ratings database or a ready-to-run map SaaS.

## Flexible Inputs

No screenshot, flight booking, hotel or exact date is required. Start with just a destination. The skill suggests trip lengths, explains neighborhoods and attractions, and drafts clearly labeled sample itineraries.

It supports one-way, return and multi-city flights; fully booked, partially booked or undecided accommodation; and fixed appointments, rest periods or work commitments. Unknown facts remain unknown instead of becoming invented bookings.

## What it does

- Compares routes with meaningful trade-offs and realistic transport buffers.
- Explains attractions, photography locations and walking routes.
- Organizes food candidates by category, location and suitability, not rating alone.
- Records Google rating sources, review counts and verification dates; distinguishes direct checks from third-party snapshots.
- Adds genuine business or food photos with attribution and loading fallbacks.
- Produces an interactive map with day and segment views, optional food layers and scrollable popups.
- Generates Chinese and English HTML content with a language switch, shared map data and preserved selection state.
- Supports publishing when explicitly requested and an authorized hosting service is available.

## Install and use

Place this entire repository folder at ~/.codex/skills/planning-travel-maps, or in the equivalent skills directory for your Codex installation. Keep SKILL.md and its references together.

Example:

> Use $planning-travel-maps to plan a relaxed trip to Penang. I have not chosen dates or a hotel yet. Explain the options first.

Another example:

> I have booked a one-way flight and my first two hotel nights. Build on those commitments, suggest the remaining itinerary, and create a bilingual interactive map.

## Files

SKILL.md is the entry point. The references directory contains input handling, research and routing, food selection, data conventions, map publishing, localization and trial scenarios. agents/openai.yaml provides Codex interface metadata.

Instructions are primarily written in Chinese; they explicitly require complete Chinese and English HTML output. This package is a workflow skill, not a prebuilt website or a standalone app.

## Requirements and limitations

The host needs browsing or search capabilities to verify changing information, file tools to generate artifacts, and browser capabilities for visual testing. Deployment requires a hosting provider and appropriate authorization. No accounts, credentials, map quotas or paid services are included.

Ratings are dated snapshots, not a live data feed. Maps, photos and external navigation may require internet access. Language switching uses embedded translations and should not require a translation service.

The skill does not automatically purchase tickets, reserve hotels or restaurants, or publish personal travel information. It does not promise permanent hosting. This repository contains no personal bookings or trip screenshots. Trial scenarios are test suggestions, not claims of completed end-to-end testing.
