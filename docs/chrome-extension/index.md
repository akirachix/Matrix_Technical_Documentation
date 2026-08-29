# Chrome Extension / Frontend

## Frontend technology

The supplied extension uses:

- React
- React DOM
- Vite
- `@crxjs/vite-plugin`
- Manifest V3
- Chrome extension APIs

## Main folder structure

```
src/
├── api/
│   └── client.js
├── background/
│   ├── authManager.js
│   ├── background.js
│   ├── messageHandler.js
│   └── sessionManager.js
├── commands/
│   ├── commandDictionary.js
│   └── commandInterpreter.js
├── components/
│   ├── AccountButton.jsx
│   ├── AccountMenu.jsx
│   ├── ReaderControls.jsx
│   └── Stats.jsx
├── content/
│   ├── commentDetector.js
│   ├── content.js
│   ├── imageDetector.js
│   └── reader.js
├── metrics/
│   └── metrics.js
├── pages/
│   ├── ForgotPassword.jsx
│   ├── Login.jsx
│   └── Signup.jsx
├── speech/
│   ├── speechRecognition.js
│   ├── speechSynthesis.js
│   └── voiceProfiles.js
├── utils/
│   └── storage.js
└── App.jsx
```

## Where new code goes

| Change | Location |
|---|---|
| Popup UI component | `src/components/` |
| Popup page | `src/pages/` |
| Webpage DOM processing | `src/content/` |
| Background/browser coordination | `src/background/` |
| Speech functionality | `src/speech/` |
| Command logic | `src/commands/` |
| API client logic | `src/api/` |
| Metrics | `src/metrics/` |
| Storage helpers | `src/utils/` |

!!! warning
    Do not put webpage DOM logic into React popup components.
    Do not put React components into the service worker.
    Follow the existing responsibility boundaries when adding new code.

## Popup

The primary popup application is `src/App.jsx`. It provides access to:

- reader controls;
- speech settings;
- image-description settings;
- purification settings;
- voice-command settings;
- theme/brightness settings;
- account functionality.

## Settings storage

Persistent reader settings use `chrome.storage.local`.

The current settings key is `secureReaderSettings`.

Storage helpers are in `src/utils/storage.js`.

## Authentication session storage

Authentication session state uses `chrome.storage.session` with key `secureReaderSession`.

Authentication/session code is in:

- `src/background/authManager.js`
- `src/background/sessionManager.js`
