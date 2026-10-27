---
layout: page
title: Fotr - Privacy Policy
---

# Privacy Policy for Fotr

**Last updated: October 27, 2026**

## Overview

Fotr is a local-first photo viewing application. It runs entirely on your
computer. Your photos and data stay on your machine. Fotr has no server
component, no cloud backend, no user accounts, and no data collection.

## Google User Data: Access

When you optionally connect your Google Photos account, Fotr requests access
to the following Google user data via the `photoslibrary.readonly` OAuth scope:

- **Media item metadata** -- titles, descriptions, creation dates, and
  dimensions of your photos and videos as returned by the Google Photos
  Library API
- **Media item content** -- the photo and video files themselves, downloaded
  at full resolution via the `baseUrl` provided by the API

Fotr does **not** access any other Google services or data. It does not access
your Google Drive, Gmail, Contacts, Calendar, or any other account information
beyond what is listed above.

No aggregated or anonymized Google user data is created or stored by Fotr.
All data is stored in its original, raw form on your local machine.

## Google User Data: Use

Google user data accessed by Fotr is used exclusively for the following
purposes:

- **Local display** -- showing your photos in the timeline, album, map, and
  detail views within the Fotr application on your computer
- **Local indexing** -- extracting metadata (dates, GPS coordinates,
  descriptions) and storing it in a local SQLite database to enable
  searching, sorting, and filtering
- **Local thumbnailing** -- generating smaller preview images cached on your
  local disk for faster browsing

All processing happens locally on your machine. Google user data is never
used for advertising, profiling, analytics, machine learning training, or any
purpose other than displaying your photos to you.

## Google User Data: Transfer

Fotr does **not** transfer, share, sell, or disclose your Google user data
to any third party, for any reason, under any circumstances. Specifically:

- No Google user data is sent to any server operated by the developer or
  any third party
- No Google user data is shared with advertisers, analytics providers,
  data brokers, or any other entity
- No Google user data is used to serve advertising or for remarketing
- No Google user data leaves your local machine after being downloaded

The only network communication involving your Google data is between
your computer and Google's API servers during the sync process.

## Google User Data: Protection

Google user data stored by Fotr is protected as follows:

- **Local-only storage** -- all downloaded photos, metadata, and thumbnails
  are stored on your local file system in the archive directory you choose
- **OAuth tokens** -- access and refresh tokens are stored in a local
  configuration file on your machine:
  - macOS: `~/Library/Application Support/com.andrewdavidmackenzie.fotr/config.toml`
  - Linux: `~/.config/fotr/config.toml`
  - Windows: `%APPDATA%\andrewdavidmackenzie\fotr\config\config.toml`
- **Encrypted transport** -- all communication with Google's API uses HTTPS
  (TLS encryption in transit)
- **No remote storage** -- Fotr has no server, no database, and no cloud
  storage. There is no remote attack surface for your data.
- **Open source** -- Fotr's complete source code is publicly available at
  [github.com/andrewdavidmackenzie/fotr](https://github.com/andrewdavidmackenzie/fotr)
  so anyone can verify exactly how data is handled

Token security relies on your operating system's file permissions. Fotr does
not implement additional encryption of stored tokens. You are responsible
for securing access to your computer and user account.

## Google User Data: Retention and Deletion

- **Downloaded photos** remain on your local machine indefinitely until you
  choose to delete them. Fotr does not automatically delete downloaded photos.
- **OAuth tokens** are retained until you explicitly disconnect from Google
  Photos or delete the config file.
- **Indexed metadata** (the local SQLite database) is retained until you
  delete the `.fotr.db` file or the archive directory.

To delete all Google user data from your machine:

1. **Disconnect** from Google Photos in Fotr's Services panel -- this removes
   the stored OAuth tokens from the config file
2. **Revoke access** at
   [myaccount.google.com/permissions](https://myaccount.google.com/permissions)
   -- this prevents any further access even if tokens remain
3. **Delete downloaded photos** by removing the sync subdirectory
   (e.g. `google_photos/`) from your archive, or delete the entire archive
4. **Delete the database** by removing the `.fotr.db` file and
   `.fotr-thumbs/` directory from your archive

After disconnecting and revoking access, Fotr cannot access your Google Photos
account. Previously downloaded files remain on your local disk until you
manually delete them.

## Local Photo Archives

In addition to the optional Google Photos integration, Fotr accesses local
files on your machine:

- Fotr reads photo and video files from a directory you select
- It creates a local SQLite database (`.fotr.db`) in your archive directory
  to index metadata (dates, locations, descriptions, file sizes)
- It generates thumbnail images (`.fotr-thumbs/`) for faster display
- All of this data stays on your local machine

## What Data Fotr Does NOT Collect

- Fotr does **not** collect any personal information
- Fotr does **not** have any analytics, telemetry, or tracking
- Fotr does **not** store any data in the cloud or on remote servers
- Fotr does **not** create user accounts or profiles
- Fotr does **not** use cookies

## Network Access

Fotr makes network requests only for:

- **Google Photos API** -- only when you explicitly connect and sync (optional).
  Uses HTTPS to `photoslibrary.googleapis.com`
- **Google OAuth** -- only during the authorization flow (optional).
  Uses HTTPS to `accounts.google.com`
- **OpenStreetMap tiles** -- map background images, fetched via HTTPS from
  `tile.openstreetmap.org`
- **Nominatim geocoding** -- converting GPS coordinates to place names,
  via HTTPS to `nominatim.openstreetmap.org`

All network requests use HTTPS. No data is sent to any server operated by
the developer.

## Changes to This Policy

This privacy policy may be updated from time to time. The "Last updated" date
at the top of this page indicates when the policy was last revised. Continued
use of Fotr after changes constitutes acceptance of the updated policy.

## Open Source

Fotr is open source software licensed under the
[MIT License](https://github.com/andrewdavidmackenzie/fotr/blob/main/LICENSE).

## Contact

For privacy questions, contact: andrew@mackenzie-serres.net
