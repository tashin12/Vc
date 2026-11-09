# VoiceStudio integration bootstrap for tashin12/Vc

This package adds an automated importer for the **official** upstream repository:
https://github.com/debpalash/VoiceStudio

## What happens

After you upload these files to the `main` branch of `tashin12/Vc`, the GitHub
Actions workflow downloads the current upstream `main` source and commits it
into the `VoiceStudio/` directory in your repository.

Your existing files at the repository root are preserved. The imported app
remains in its own folder, so its original project structure is not flattened.

## Upload steps

1. Extract this ZIP.
2. In `https://github.com/tashin12/Vc`, choose **Add file → Upload files**.
3. Upload the `.github` folder and `README-VoiceStudio-Integration.md`.
   Make sure `.github/workflows/import-voicestudio.yml` keeps its exact path.
4. Commit the upload to the `main` branch.
5. Open the repository's **Actions** tab and wait for **Import VoiceStudio upstream**.
6. When it finishes, you should see the full upstream source in `VoiceStudio/`.

If the workflow does not run automatically, open Actions → Import VoiceStudio
upstream → Run workflow.

## Important: hosting

This imports the real source code; it does **not** make the complete VoiceStudio
AI engine run on Vercel. Upstream VoiceStudio is a local-first desktop app with
a Python inference backend and downloadable model weights. Its own README
documents desktop installers and a Docker deployment. Vercel's serverless
runtime is not a replacement for that persistent model-running backend.

For the full web-accessible VoiceStudio experience, use a persistent
Linux/Docker host for the official container/backend. You can still use Vercel
for a separate static landing page or frontend if you build one to connect to
that backend.

## API keys

The importer itself needs no third-party API key. GitHub Actions uses the
repository's built-in `GITHUB_TOKEN` with `contents: write` permission, granted
by the workflow. VoiceStudio's official Docker instructions separately
describe its local API authentication setting; this package does not invent or
hardcode a key.

## Licensing

VoiceStudio is licensed under AGPL-3.0. The imported source retains its upstream
license and notices. Review the license and the upstream model/voice licenses
before redistributing or deploying it.
