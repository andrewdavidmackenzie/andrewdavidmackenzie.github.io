---
layout: page
title: Fotr - Privacy Policy
---

# Privacy Policy for Fotr

**Last updated: October 26, 2026**

## Overview

Fotr is a local-first photo viewing application. Your photos and data stay on your machine.

## What Data Fotr Accesses

### Local Photo Archives
- Fotr reads photo and video files from a directory you select on your local machine
- It creates a local SQLite database (`.fotr.db`) in your archive directory to index metadata
- It generates thumbnail images (`.fotr-thumbs/`) in your archive directory for faster display
- All of this data stays on your local machine

### Google Photos (Optional)
- If you choose to connect your Google Photos account, Fotr accesses your Google Photos library in **read-only** mode using the `photoslibrary.readonly` scope
- Fotr downloads photos from Google Photos to your local archive directory
- Fotr does **not** modify, delete, or upload anything to your Google Photos account

### OAuth Tokens
- When you connect to Google Photos, OAuth access and refresh tokens are stored in a local configuration file on your machine
- On macOS: `~/Library/Application Support/com.andrewdavidmackenzie.fotr/config.toml`
- On Linux: `~/.config/fotr/config.toml`
- On Windows: `%APPDATA%\andrewdavidmackenzie\fotr\config\config.toml`
- Tokens are stored in plain text in the config file. They are not transmitted to any third party.

## What Data Fotr Does NOT Collect

- Fotr does **not** send any data to any server (other than Google's API when syncing)
- Fotr does **not** have any analytics, telemetry, or tracking
- Fotr does **not** store any data in the cloud
- Fotr does **not** share your data with any third party

## Network Access

Fotr makes network requests only for:
- **OpenStreetMap tiles** — map background images, fetched from `tile.openstreetmap.org`
- **Nominatim geocoding** — converting GPS coordinates to place names and vice versa, via `nominatim.openstreetmap.org`
- **Google Photos API** — only when you explicitly connect and sync (optional)
- **Google OAuth** — only during the authorization flow (optional)

All network requests use HTTPS.

## Data Deletion

- Disconnect from Google Photos in the Services panel to remove stored tokens
- Delete the config file to remove all stored settings
- Delete the `.fotr.db` file and `.fotr-thumbs/` directory to remove all indexed data
- Fotr never modifies your original photo files (except when you explicitly request operations like deletion)

## Open Source

Fotr is open source software licensed under the MIT License.

## Contact

For privacy questions, contact: andrew@mackenzie-serres.net
