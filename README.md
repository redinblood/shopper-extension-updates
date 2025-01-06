# Shopper Intelligence Chrome Extension

This repository hosts the Chrome extension for accessing Similarweb's Shopper Intelligence directly from Amazon product pages, along with its update infrastructure.

## Installation

1. Download the latest `shopper-intelligence.crx` file from [here](https://github.com/TalMilnerSimilar/shopper-extension-updates/raw/main/shopper-intelligence.crx)
2. Open Chrome and navigate to `chrome://extensions/`
3. Enable "Developer mode" (toggle in top right)
4. Drag and drop the downloaded `.crx` file into the extensions page

## Auto-Updates

The extension is configured to automatically check for and install updates. When a new version is released:
1. The extension will automatically detect the update
2. Chrome will download and install the new version
3. You may need to restart Chrome to activate the update

## For Developers

To release a new version:
1. Update the version number in `manifest.json` (e.g., from "1.0" to "1.1")
2. Pack the extension in Chrome to create a new `.crx` file
3. Rename the new `.crx` file to `shopper-intelligence.crx`
4. Update the version in `updates.xml` to match the new version in manifest.json
5. Push the changes to this repository

Note: Version numbers should follow semantic versioning (e.g., "1.0", "1.1", "2.0"). The version in `manifest.json` and `updates.xml` must match exactly for auto-updates to work.

## Files
- `manifest.json`: Extension configuration
- `content.js`: Main extension logic
- `updates.xml`: Auto-update manifest
- `shopper-intelligence.crx`: Packaged extension file (latest version)
- `icon48.png`, `icon128.png`: Extension icons


