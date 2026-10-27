---
layout: page
title: Fotr - Local Photo Viewer
---

# Fotr

A local photo viewing application for Google Photos Takeout archives and cloud
photo services. Fotr runs entirely on your computer -- your photos stay on your
machine, and all browsing, searching, and editing happens locally.

## Features

- **Timeline view** with chronological photo grid, year/month navigation, and infinite scroll
- **Album management** with covers, creation, renaming, and photo organization
- **Map view** with OSM tiles, photo clustering, and geocoded locations
- **Search** by filename, description, date range, and album
- **Google Photos sync** to download photos from your Google Photos library
- **Import** photos, directories, and zip archives into your local archive
- **Date and location editing** with inline editors and forward geocoding
- **Duplicate detection** with content hashing and auto-resolve
- **Video support** with thumbnail extraction and native playback
- **HEIC/HEIF conversion** for iPhone photos
- **22 languages** with automatic OS locale detection
- **Dark/Light/System theme** with automatic OS detection

## Google Photos Integration

Fotr can optionally connect to your Google Photos account to download your
photos to your local machine. This is entirely optional -- Fotr works fully
without any Google account.

### What Fotr accesses

Fotr requests **read-only** access to your Google Photos library using the
`photoslibrary.readonly` OAuth scope. This means Fotr can:

- **List** your photos and albums
- **Download** photos and videos to your local archive

Fotr **cannot** and **does not**:

- Upload, modify, or delete any photos in your Google Photos account
- Access any other Google services (Drive, Gmail, Contacts, etc.)
- Share your photos or data with any third party
- Collect analytics, telemetry, or tracking data

### How it works

1. You click "Connect Google Photos" in the Services panel
2. Your browser opens to Google's consent screen where you authorize Fotr
3. Fotr receives an OAuth token and stores it locally in your config file
4. When you click "Sync", Fotr downloads new photos to your local archive
5. Downloaded photos are indexed and appear in your timeline, map, and albums

### Revoking access

You can revoke Fotr's access to your Google Photos at any time:

- **In Fotr**: click "Disconnect" in the Services panel to remove stored tokens
- **In Google**: visit [myaccount.google.com/permissions](https://myaccount.google.com/permissions)
  and remove Fotr from your authorized applications

Revoking access immediately prevents Fotr from accessing your Google Photos.
Photos already downloaded to your local archive remain on your machine.

### Data handling

- OAuth tokens are stored only on your local machine in a config file
- Tokens are never transmitted to any server other than Google's API
- Downloaded photos are stored in your local archive directory
- Fotr has no server component -- there is no cloud backend, no user accounts,
  and no data collection
- Fotr is [open source](https://github.com/andrewdavidmackenzie/fotr) (MIT License)
  -- you can inspect exactly what the code does

For full details, see our [Privacy Policy](/fotr/privacy).

## Screenshots

Coming soon.

## Download

Fotr is available for macOS, Linux, and Windows from the
[GitHub Releases](https://github.com/andrewdavidmackenzie/fotr/releases) page.

## Source Code

Fotr is open source software licensed under the
[MIT License](https://github.com/andrewdavidmackenzie/fotr/blob/main/LICENSE).
The full source code is available on
[GitHub](https://github.com/andrewdavidmackenzie/fotr).

## Privacy Policy

See the [Privacy Policy](/fotr/privacy) for details on how Fotr handles your data.

## Terms of Service

See the [Terms of Service](/fotr/terms) for usage terms.

## Support

For bug reports and feature requests, please
[open an issue](https://github.com/andrewdavidmackenzie/fotr/issues) on GitHub
or contact: andrew@mackenzie-serres.net
