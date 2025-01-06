# How to Update the Extension

This document outlines the step-by-step process for creating and deploying a new version of the Shopper Intelligence Chrome extension.

## Prerequisites

- Access to the GitHub repository
- The private key file (`Shopper Chrome extention.pem`)
- Chrome browser with Developer Mode enabled

## Update Process

### 1. Create a New Branch
```bash
# Create and checkout a new branch
git checkout -b version-X.X
```

### 2. Update Version Numbers
1. Edit `manifest.json`:
   - Update `"version"` to new version number
   - Update `"name"` to include new version (optional)

2. Edit `updates.xml`:
   - Update `version` attribute in `<updatecheck>` tag

### 3. Package the Extension
1. Create a clean directory for the new version:
   ```bash
   mkdir -p ../extension_vX.X
   cp manifest.json content.js icon48.png icon128.png "../extension_vX.X/"
   ```

2. In Chrome:
   - Go to `chrome://extensions/`
   - Enable Developer Mode
   - Click "Pack extension"
   - Set "Extension root directory" to your new version directory
   - Set "Private key file" to `Shopper Chrome extention.pem`
   - Click "Pack Extension"

### 4. Deploy the Update
1. Move the new `.crx` file:
   ```bash
   mv ../extension_vX.X.crx shopper-intelligence.crx
   ```

2. Commit and create pull request:
   ```bash
   git add shopper-intelligence.crx manifest.json updates.xml
   git commit -m "Update extension to version X.X"
   git push origin version-X.X
   ```

3. Go to GitHub:
   - Create a pull request from your branch
   - Review changes
   - Merge to main

### 5. Verify the Update
1. In Chrome:
   - Go to `chrome://extensions/`
   - Find "Shopper Intelligence on Amazon"
   - Toggle Developer Mode off and on
   - Verify version number updates

## Important Notes

- Keep the `.pem` file secure and never commit it to Git
- Always create updates through pull requests
- Test the extension before pushing to main
- Back up the `.pem` file - without it, you cannot push updates

## Troubleshooting

If updates aren't working:
1. Check `chrome://extensions-internals/` for your extension
2. Verify the update URL is correct
3. Ensure the `.crx` file is properly signed
4. Check that version numbers match in both files 