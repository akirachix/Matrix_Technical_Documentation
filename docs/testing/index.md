# Testing and QA

## Existing QA documentation

The project already has dedicated testing evidence:

- [Test Scenarios and Test Cases](https://docs.google.com/spreadsheets/d/1HZEHZXPVk12cdFQLBZztsD4yPVLhykx85_LrxtLIeB0/edit?gid=400157956#gid=400157956)
- [API and Integration Testing](https://github.com/akirachix/Matrix_Backend/tree/postman-tests)
- [Informational Website TDD](https://github.com/akirachix/Matrix_Informational_Website/tree/feature/testcase)
- [Usability Testing](https://docs.google.com/document/d/1sHpzLYos9pYdKLo-ahYypCzHlPNVBYcdYV0ZHeFWc3g/edit?tab=t.0)

## Extension automated testing

No dedicated automated Chrome-extension test suite is confirmed in the supplied extension source.

> Automated extension test coverage is not confirmed.

## Build test

```bash
npm run build
```

This verifies the extension can be packaged.

## Lint test

```bash
npm run lint
```

Current state: **known lint failures exist.**

## Manual reader tests

- normal article;
- page with `main`;
- page with `article`;
- page using `[role="main"]`;
- page without a specialised content container;
- page with navigation;
- long page;
- different languages;
- stop/restart.

## Speech tests

- volume;
- speed;
- Default profile;
- Clear profile;
- Calm profile;
- exact language voice available;
- exact language voice unavailable;
- fallback voice.

## Image tests

- one image;
- multiple images;
- image with alt text;
- image without alt text;
- image from the same origin;
- cross-origin image;
- inaccessible image;
- broken image;
- image with zero dimensions;
- Gemini Nano unavailable;
- Gemini Nano available;
- generated description spoken;
- one failed image followed by readable text.

## Authentication tests

- signup;
- invalid signup;
- login;
- invalid login;
- logout;
- forgot password;
- reset password;
- change password;
- profile retrieval;
- profile update;
- session behaviour.

## Purification tests

Test purification against supported comments, not entire webpages:

- non-toxic supported comment;
- low-toxicity comment;
- medium/high toxicity comment;
- ordinary webpage paragraph;
- supported comment detection;
- unsupported page content.

The desired behaviour is that ordinary webpage content is not treated as a comment.

## Metrics tests

- allowed metric;
- disallowed metric;
- authenticated metrics request;
- backend failure;
- metric count.

## Usability evidence

The [Usability Testing document](https://docs.google.com/document/d/1sHpzLYos9pYdKLo-ahYypCzHlPNVBYcdYV0ZHeFWc3g/edit?tab=t.0) should be referenced for evidence about how real users interact with the product.

## Troubleshooting

| Problem                     | Error / symptom                                               | Likely cause                                                               | Current response                                                            |
| --------------------------- | ------------------------------------------------------------- | -------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Image cannot be accessed    | `DOMException: The image cannot be accessed by the extension` | Browser/extension image-access restriction                                 | Treat as known issue; investigate image source/accessibility handling.      |
| Gemini Nano unavailable     | Availability returns unavailable                              | Browser/device/model environment does not currently support the capability | Test using a supported Chrome environment and verify built-in AI readiness. |
| Model not ready             | AI cannot create a session                                    | Required model resources may not be ready                                  | Check Chrome built-in AI readiness and model download status.               |
| Image failure stops reading | Reader fails before speech                                    | Current image-processing error is not safely isolated                      | Fix error isolation so text reading can continue.                           |
| Profile update fails        | `Unsupported API action`                                      | Popup action does not match service-worker route mapping                   | Align action name and backend route handling.                               |
| Lint fails                  | ESLint errors                                                 | Existing source/configuration problems                                     | Fix or explicitly configure valid exceptions, then rerun lint.              |
| Build fails                 | Vite/npm error                                                | Dependency/configuration/environment problem                               | Run `npm install`, inspect first error, verify Node/npm version.            |
| No matching voice           | Unexpected/fallback voice                                     | Browser does not provide requested voice                                   | Use fallback voice matching.                                                |
| Wrong AI language           | Description falls back to English                             | Current model language mapping does not cover requested language           | Use supported model language or extend mapping.                             |
