# GamePanel

GamePanel is a self-hosted game-server administration project currently under active development.

This repository is a **public project overview** for third-party service integrations. The main development repository is private while the project is being built; no private source code, credentials, internal infrastructure details, or user/server data are published here.

## Minecraft content workflow

One part of GamePanel focuses on helping a server administrator understand the Minecraft content already installed on a server.

The intended workflow is conservative:

- inspect files that already exist on the administrator's own server;
- compute local hashes/fingerprints;
- identify a file only when a reliable source can match it;
- keep uncertain results explicitly unknown instead of guessing;
- help the administrator build a client-content manifest describing what a connecting client may need.

A GamePanel manifest is metadata generated from the administrator's own server state. It is not intended to be a mirror or replacement for a mod distribution platform.

## Planned CurseForge integration

The CurseForge API integration is intended to provide **exact file identification and provenance** for Minecraft JARs that are already present locally.

The expected use is:

1. GamePanel computes a fingerprint locally.
2. The fingerprint is submitted to the official CurseForge API.
3. When CurseForge returns an exact match, GamePanel can use the response to identify the corresponding CurseForge project/file and present that provenance to the administrator.
4. If no reliable match exists, GamePanel keeps the result unresolved rather than falling back to filename-based guessing.

The integration is deliberately not intended to:

- crawl or bulk-index the CurseForge catalog;
- scrape CurseForge web pages;
- bypass CurseForge author distribution settings;
- provide an alternate mirror for CurseForge-hosted files;
- expose or share an API key;
- build a product that competes with CurseForge.

Any API use will be implemented within the current CurseForge API terms and documented limits. API-derived data will not be persisted or cached where the applicable terms prohibit it.

## Distribution and author control

GamePanel is designed to respect author and platform controls.

If a CurseForge project/file is not available for third-party distribution, GamePanel will not attempt to bypass that restriction. The administrator should be directed back to the authorized source rather than receiving an independently rehosted copy.

Where the official API permits access or delivery, GamePanel will follow the API-provided behavior and applicable author settings.

## Security

CurseForge API credentials are expected to be treated as secrets and kept outside public repositories, client-side bundles, logs, generated manifests, and screenshots.

## Public repository scope

This repository intentionally contains documentation only. It does **not** expose GamePanel's private implementation, internal architecture, database design, infrastructure, roadmap, test environments, or operational data.

For the planned CurseForge API usage, see [docs/curseforge-api.md](docs/curseforge-api.md).
