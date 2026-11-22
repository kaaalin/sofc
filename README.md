# SOF Airside — GitHub + Vercel edition

Bilingual Terminal 2 passenger assistant prototype with all 50 supplied passenger questions. This package contains the working static website, its source code, tests, and Vercel deployment configuration.

## Upload to GitHub

1. Extract `sof-airside-vercel.zip` on your computer.
2. Create a new GitHub repository.
3. Choose **uploading an existing file**, or **Add file → Upload files** in an existing repository.
4. Drag the extracted contents into GitHub. Upload `dist` as a folder, plus the root files. Do not upload only the ZIP.
5. Confirm that `vercel.json`, `package.json`, and `README.md` are at the repository root, with `dist/index.html` below them. Commit the files.

The ZIP has no enclosing parent folder, so extracting its contents directly into your repository preserves the correct layout. If your unzip program creates a wrapping folder automatically, upload the contents of that folder.

## Connect to Vercel

1. In Vercel, choose **Add New → Project** and import your GitHub repository.
2. Keep the **Root Directory** at the repository root.
3. Use **Other** as the Framework Preset. The included `vercel.json` configures:
   - Build Command: empty (no build required)
   - Install Command: empty (no dependencies)
   - Output Directory: `dist`
4. No environment variables or API keys are required.
5. Click **Deploy** and open the resulting deployment URL.

Configuration reference: https://vercel.com/docs/builds/configure-a-build

This export is standalone and does not use the ChatGPT Site access gate. Access to your Vercel deployment depends on your Vercel project settings.

## Local preview

Serve the `dist` directory with a local HTTP server, for example:

```sh
python -m http.server 8080 --directory dist
```

Open http://localhost:8080 in your browser. Opening the HTML directly as a file will not load the question library correctly.

## Verify

With Node.js installed:

```sh
npm test
```

No package installation is required. Tests cover all 50 CSV routes and selected follow-ups, guardrails, unavailable data and operational scenarios. Passing these tests is not an answer-accuracy certification.

## Edit the prototype

- `dist/index.html`: layout and content structure
- `dist/style.css`: appearance and responsive layout
- `dist/app.js`: interface and interaction logic
- `dist/knowledge.js`: bilingual answers, sources, demo flights and intent rules
- `dist/questions.json`: all 50 passenger questions
- `tests.mjs`: functional checks
- `vercel.json`: hosting settings

See `PROTOTYPE.md` for detailed behavior, limitations and production integration requirements.

Flight data, airport facilities, routes and handovers remain illustrative. No live flight feeds, Azure services, LLM answering or real staff queues are connected.
