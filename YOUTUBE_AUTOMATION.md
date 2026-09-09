# YouTube Automation (AgentTube)

The `youtube-automation/` folder contains [AgentTube](https://github.com/darkzOGx/youtube-automation-agent) (a.k.a. `youtube-automation-agent`), an open-source AI agent that can run a YouTube channel end to end: research, scripting, narration/video generation, thumbnails, SEO, scheduled publishing, and analytics — with human approval gates before anything publishes.

It is installed here as a standalone Node.js app inside this repo. Its dependencies were installed but `node_modules/` is git-ignored, so you need to run `npm install` again after cloning/pulling.

## Setup (you need to do this part)

The tool needs credentials only you can provide — there's no way to generate these on your behalf:

1. **Install dependencies**
   ```bash
   cd youtube-automation
   npm install
   ```

2. **Fill in your API keys.** A `.env` file was created from `.env.example` (not committed to git). Open `youtube-automation/.env` and fill in at least:
   - One AI text provider key: `OPENAI_API_KEY`, `GEMINI_API_KEY`, `OPENROUTER_API_KEY`, `MOONSHOT_API_KEY`, `MIMO_API_KEY`, or `GLM_API_KEY`
   - `CHANNEL_NAME` / `TARGET_AUDIENCE` for your channel
   - Optionally `ELEVENLABS_API_KEY` (premium TTS) and `REPLICATE_API_TOKEN` (AI video generation)

3. **YouTube Data API credentials.** Create a Google Cloud project, enable the YouTube Data API v3, and set up OAuth credentials. Full steps are in `youtube-automation/README.md`.

4. **Guided setup / first run**
   ```bash
   npm run walkthrough   # interactive, guides provider selection + YouTube auth
   # or
   npm run setup         # faster path if you're already familiar
   npm start              # launches the dashboard at http://localhost:3456
   ```

## Notes

- `npm audit` currently reports vulnerabilities in upstream dependencies of this third-party tool (mostly transitive). Run `npm audit fix` inside `youtube-automation/` if you want to address them, or check the upstream project for updates.
- Nothing in this tool is wired into the `jyamagazine` static site itself (`index.html` / `admin/`) — it's an independent app living alongside it in this repo.
