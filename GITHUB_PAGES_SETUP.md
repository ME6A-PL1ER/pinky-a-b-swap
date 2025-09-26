# GitHub Pages Setup for Pinky NES Emulator

This repository now includes a GitHub Actions workflow to automatically build and deploy the Pinky web emulator to GitHub Pages.

## Setup Instructions

### 1. Enable GitHub Pages (Required Action)
**You need to complete this step manually in the repository settings:**

1. Go to your repository Settings: `https://github.com/ME6A-PL1ER/pinky-a-b-swap/settings`
2. Navigate to "Pages" in the left sidebar
3. Under "Source", select **"GitHub Actions"** (not "Deploy from a branch")
4. Click "Save"

### 2. Automatic Deployment
- The workflow will automatically trigger on pushes to the `master` branch
- It builds the WebAssembly version of the emulator using `cargo-web`
- Deploys the static files and built assets to GitHub Pages
- The build includes multiple fallback strategies for compatibility

### 3. Accessing the Emulator
After deployment and setup, the emulator will be available at:
**https://ME6A-PL1ER.github.io/pinky-a-b-swap/**

The page includes:
- The NES emulator running in WebAssembly
- Built-in ROM files for testing
- Game controls and ROM loading interface

## Repository Changes Made

✅ **GitHub Actions Workflow**: `.github/workflows/deploy-pages.yml`
- Builds the Rust WebAssembly code using `cargo-web`
- Handles stdweb compatibility issues
- Includes fallback build strategies
- Deploys to GitHub Pages automatically

✅ **Updated Links**: 
- `README.md` now points to the correct GitHub Pages URL
- `pinky-web/static/index.html` updated with correct repository links
- Added GitHub Actions badge

✅ **Documentation**: `GITHUB_PAGES_SETUP.md` (this file)

## Technical Details

- **Build System**: Uses `cargo-web` to build Rust code to WebAssembly with `stdweb` bindings
- **Compatibility**: Uses Rust 1.70.0 and Ubuntu 20.04 for better `stdweb` compatibility  
- **Fallback Strategy**: Multiple build attempts with error handling
- **Static Assets**: Includes CSS, ROM files, HTML, and generated JS/WASM

## Manual Build (for local testing)

```bash
# Install cargo-web
cargo install cargo-web --version 0.6.26

# Build the project
cd pinky-web
cargo web build --release

# Serve locally (optional)
cargo web start --release
# Then visit http://localhost:8000
```

## Next Steps

1. **Enable GitHub Pages** in repository settings (see step 1 above)
2. Push/merge this branch to `master` to trigger the first build
3. Check the Actions tab for build status
4. Visit the GitHub Pages URL once deployment completes

## Troubleshooting

- **Build failures**: Check the Actions tab for detailed logs
- **Page not loading**: Ensure GitHub Pages is set to "GitHub Actions" source
- **JavaScript errors**: The workflow includes fallback JS generation for build issues
- **404 errors**: Make sure the branch with the workflow is merged to `master`

## Status

🟡 **Setup Complete - Awaiting Repository Configuration**
- GitHub Actions workflow is ready
- Code changes are committed  
- **Manual step required**: Enable GitHub Pages in repository settings