# Product and Project References

## Product research

- [Problem and Solution Research](https://docs.google.com/presentation/d/1aoW5dxqPRSnOgqgC-Zd-hHDyUUPBEWXMJgV4vBmwBqg/edit?slide=id.g3e76be32d27_2_75#slide=id.g3e76be32d27_2_75)
- [SWOT Analysis](https://docs.google.com/document/d/1jRlvZfQjtglDCExHWiXNiWKk8ZGmHwrLTnBGcyIsqUc/edit?tab=t.0#heading=h.oqa7l1cy2786)
- [Informational Website](https://matrix-informational-website-4wyi.vercel.app/)

## Design

- **FigJam (product/UI designs):** [SecureReader FigJam Board](https://www.figma.com/board/Hp55xeeCbfXaKqw80e8Msv/Matrix?node-id=0-1&t=jiv92gvgyCHdED8V-0)

## Architecture and security

- [Cyber Security SAD](https://miro.com/app/board/uXjVHyBAoK0=/)
- [SAD](https://lucid.app/lucidchart/c82a2e14-a27e-40cd-9c57-6490bf73eae1/edit?invitationId=inv_c3bd121b-0e1f-433d-a1d3-6ac2f1ff2416&page=0_0#)
- [ERD](https://docs.google.com/document/d/1bwScVpZCh8B_trL5izIKHlrFW-PT39U_f7wSsHbguFY/edit?tab=t.0#heading=h.6fxiynwr0aa5)

## Backend

- [API Documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs)
- [API and Integration Tests](https://github.com/akirachix/Matrix_Backend/tree/postman-tests)

## QA and UX

- [Test Scenarios and Test Cases](https://docs.google.com/spreadsheets/d/1HZEHZXPVk12cdFQLBZztsD4yPVLhykx85_LrxtLIeB0/edit?gid=400157956#gid=400157956)
- [Usability Testing](https://docs.google.com/document/d/1sHpzLYos9pYdKLo-ahYypCzHlPNVBYcdYV0ZHeFWc3g/edit?tab=t.0)
- [Informational Website TDD](https://github.com/akirachix/Matrix_Informational_Website/tree/feature/testcase)

## Project management

- [Jira Timeline](https://andylaique.atlassian.net/jira/software/projects/MATRIX/boards/34/timeline)
- [Sprint Event Documentation](https://docs.google.com/document/d/1NlC1aRwz8HdgvqD5H_oqdpm1HND1DBxfgQJItxbfdYU/edit?tab=t.0)

## Metrics

- [Dashboard](https://matrix-dashboard-team-2dqrynx87-nagaba-shallot1.vercel.app/)

---

## Glossary

| Term | Meaning |
|---|---|
| AI | Artificial Intelligence. SecureReader uses browser-provided AI for image descriptions and classification. |
| API | Application Programming Interface used for communication with the backend. |
| Backend | Server-side application that provides account, authentication, metrics, and other API functionality. |
| Chrome Extension | Browser software installed into Chrome to provide SecureReader functionality. |
| Content Script | Extension code that runs against webpage content and can inspect the page DOM. |
| DOM | Document Object Model; the browser representation of a webpage. |
| ERD | Entity Relationship Diagram; shows database entities and relationships. |
| Gemini Nano | Google's on-device model used by Chrome's built-in AI capabilities where supported. |
| LanguageModel | Chrome browser API used by SecureReader for built-in AI sessions. |
| Manifest V3 | Chrome's current extension architecture used by SecureReader. |
| Multimodal | AI input containing more than one modality, such as text plus an image. |
| Popup | The React UI displayed when the extension is opened. |
| QA | Quality Assurance. |
| SAD | Software Architecture Document. |
| Service Worker | Manifest V3 background component responsible for extension background tasks and messaging. |
| Speech Synthesis | Browser API for converting text to spoken audio. |
| TDD | Test documentation used by the project; the exact meaning should follow the linked project document. |
| UI | User Interface. |
| UX | User Experience. |

---

## New Developer Quick Reference

**Commands**

```bash
npm install
npm run dev
npm run build
npm run lint
```

**Build output:** `dist/`

**Main application:** `src/App.jsx`

**Reader:**
```
src/content/reader.js
```

**Image processing:**
```
src/content/reader.js
src/content/imageDetector.js
```

**Speech:**
```
src/speech/speechSynthesis.js
src/speech/voiceProfiles.js
```

**Background:**
```
src/background/background.js
src/background/messageHandler.js
src/background/authManager.js
src/background/sessionManager.js
```

**Settings:** `src/utils/storage.js`

**Backend client:** `src/api/client.js`

**Metrics:** `src/metrics/metrics.js`

**Backend:** `https://secure-reader-e8d40157a540.herokuapp.com`

**API:** [Open API documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs)

**Architecture:** [SAD](https://lucid.app/lucidchart/c82a2e14-a27e-40cd-9c57-6490bf73eae1/edit?invitationId=inv_c3bd121b-0e1f-433d-a1d3-6ac2f1ff2416&page=0_0#)

**Database:** [ERD](https://docs.google.com/document/d/1bwScVpZCh8B_trL5izIKHlrFW-PT39U_f7wSsHbguFY/edit?tab=t.0#heading=h.6fxiynwr0aa5)

**QA:** [Test Scenarios and Test Cases](https://docs.google.com/spreadsheets/d/1HZEHZXPVk12cdFQLBZztsD4yPVLhykx85_LrxtLIeB0/edit?gid=400157956#gid=400157956)
