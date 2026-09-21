# Travel Planning & Interactive Maps

[中文说明](README.md)

A reusable Codex skill that turns a destination, a text itinerary, or booking screenshots into a practical travel plan and an interactive HTML map.

## Start with what you know

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
