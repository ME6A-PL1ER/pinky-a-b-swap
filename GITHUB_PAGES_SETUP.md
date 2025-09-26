# GitHub Pages Setup for Pinky NES Emulator

This repository now includes a GitHub Actions workflow to automatically build and deploy the Pinky web emulator to GitHub Pages.

## Setup Instructions

1. **Enable GitHub Pages**:
   - Go to your repository Settings
   - Navigate to "Pages" in the left sidebar
   - Under "Source", select "GitHub Actions"
   - This will allow the workflow to deploy to GitHub Pages

2. **Automatic Deployment**:
   - The workflow will automatically trigger on pushes to the `master` branch
   - It builds the WebAssembly version of the emulator using `cargo-web`
   - Deploys the static files and built assets to GitHub Pages

3. **Accessing the Emulator**:
   - After deployment, the emulator will be available at: `https://ME6A-PL1ER.github.io/pinky-a-b-swap/`
   - The page includes the emulator with built-in ROM files for testing

## Technical Details

- Uses `cargo-web` to build the Rust code to WebAssembly with `stdweb` bindings
- Compatible with the existing `stdweb`-based codebase
- Includes all static assets (CSS, ROM files, HTML)
- Uses GitHub Actions for automated CI/CD

## Manual Build (for testing)

If you want to build the web version locally:

```bash
# Install cargo-web
cargo install cargo-web

# Build the project
cd pinky-web
cargo web build --release

# Serve locally
cargo web start --release
```

## Troubleshooting

- If the build fails, check the Actions tab for detailed logs
- The build uses Rust 1.70.0 for better compatibility with `stdweb`
- Ubuntu 20.04 is used in CI for better compatibility with older dependencies