# Getting Started

## Prerequisites

The supplied extension project requires:

- Node.js
- npm
- Google Chrome
- a local checkout of the SecureReader extension repository

The exact supported Node.js version is not confirmed in the current project materials.

## Repository

The SecureReader extension repository URL is not confirmed in the supplied materials. Clone the repository using the team's normal Git workflow.

## Install dependencies

From the extension project root:

```bash
npm install
```

## Run the development server

```bash
npm run dev
```

This starts the configured Vite development workflow.

Because SecureReader is a Chrome extension, the primary runtime test should still use the Chrome extension build.

## Build the extension

```bash
npm run build
```

The production extension is generated in `dist/`.

A successful build confirms that the Vite/Chrome-extension packaging step works. It does not prove that every runtime feature works.

## Load the extension in Chrome

1. Open Google Chrome.
2. Open the Extensions management page.
3. Enable Developer Mode.
4. Select **Load unpacked**.
5. Select the generated `dist/` folder.
6. Open SecureReader from the Chrome extension toolbar.

## Basic smoke test

- Open a webpage containing normal article text.
- Open SecureReader.
- Start the reader.
- Confirm that text is spoken.
- Change speech speed.
- Change volume.
- Change the voice profile.
- Stop reading.
- Open a page containing images.
- Enable image descriptions.
- Check whether Chrome's built-in AI is available.
- Start reading and observe image-description behaviour.

## Backend configuration

The current extension points to:

```
https://secure-reader-e8d40157a540.herokuapp.com
```

The authoritative backend API documentation is available at the [SecureReader API documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs).

No separate frontend environment-variable setup is confirmed in the supplied extension materials.

## Database setup

The Chrome extension repository does not contain a database migration/seed workflow.

The database design is documented in the [ERD](https://docs.google.com/document/d/1bwScVpZCh8B_trL5izIKHlrFW-PT39U_f7wSsHbguFY/edit?tab=t.0#heading=h.6fxiynwr0aa5).

The exact backend database engine, migration command, seed command, and local database setup are not confirmed in the supplied extension materials.

!!! warning
    Do not invent migration commands. Use the backend repository's instructions for backend development.

## Getting-started checklist

- [ ] `npm install` completes.
- [ ] `npm run build` completes.
- [ ] `dist/` is created.
- [ ] Chrome loads `dist/` as an unpacked extension.
- [ ] Popup opens.
- [ ] Text can be read aloud.
- [ ] Speech settings change the reading behaviour.
- [ ] Gemini Nano availability can be checked.
- [ ] Backend requests can be tested where account functionality is required.
- [ ] Known limitations are understood before filing new defects.