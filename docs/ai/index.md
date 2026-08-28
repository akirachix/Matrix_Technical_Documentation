# AI and Gemini Nano

## AI capabilities

The current project uses browser-local AI for:

- image descriptions
- toxicity classification
- command classification

The current priority is image description.

## How the AI is acquired and integrated

SecureReader does **not** call a separate hosted AI API for the current image-description path. It uses Chrome's built-in AI capability when the browser exposes the `LanguageModel` API and the local Gemini Nano model is available.

In practical terms, the extension checks model availability in the browser, creates a session with `LanguageModel.create(...)`, sends the image together with a text instruction, and uses the returned description in the reading flow. The model is therefore supplied by the supported Chrome built-in AI environment rather than downloaded or hosted by SecureReader itself.

```js
const availability = await LanguageModel.availability(...);
const session = await LanguageModel.create(...);
const description = await session.prompt(image, prompt);
```

The exact implementation code and prompt remain the source of truth when the integration changes.

## Why Gemini Nano

Image descriptions need to turn visual webpage content into text that can be inserted into an audio reading experience.

The project uses Chrome's built-in AI rather than implementing a separate remote image-processing API. This keeps the image-processing path inside the browser when the supported local model is available.

## LanguageModel availability

The image-description implementation first checks whether the browser exposes the `LanguageModel` capability. It then checks:

```js
LanguageModel.availability(...)
```

The feature should not assume that AI is always available. Chrome's built-in AI availability depends on browser, device, configuration, and model readiness. See [Chrome's built-in AI getting started guide](https://developer.chrome.com/docs/ai/get-started).

## Creating a session

When the model is available, SecureReader uses:

```js
LanguageModel.create(...)
```

to create an AI session. The image-description session is multimodal because it accepts both:

- text instructions
- image input

The expected response is text. Chrome documents image input for the Prompt API and describes the Prompt API as a way to use Gemini Nano in supported Chrome environments. See [Chrome Prompt API documentation](https://developer.chrome.com/docs/ai/prompt-api).

## AI lifecycle

```
Check LanguageModel
 ↓
Check availability
 ↓
Create session
 ↓
Send prompt + image
 ↓
Receive description
 ↓
Use description
 ↓
Destroy session
```

Sessions should not be kept alive unnecessarily.

## Image candidate detection

The current reader searches for HTML image elements: `<img>`.

An image is considered a candidate when it is:

- an `HTMLImageElement`;
- complete;
- non-zero width;
- non-zero height.

!!! note "Known limitation"
    The current implementation does not have a complete semantic classifier for distinguishing meaningful images from every decorative/icon/tracking image.

## Image data

The implementation obtains image data from the webpage image and supplies it to the multimodal model.

!!! warning "Key limitation"
    A webpage image being visible does not guarantee that the extension is permitted to access it as model input.

## Prompting

The image-description instruction is intended to produce:

- a short description;
- factual content;
- no invented details;
- language appropriate for the reading experience;
- content that can be spoken naturally.

The exact implementation prompt should be treated as the source-of-truth prompt and kept with the image-description code when it changes.

## Generated output

The generated text becomes a reading item similar to:

```
Image 1: [generated description]
```

It is then passed to the speech system.

## Image failures

The project has encountered errors including:

```
DOMException
The image cannot be accessed by the extension
```

This is a confirmed technical limitation and must be treated as such. The extension may display an image successfully while still being unable to access the underlying image data for the AI operation.

## Failure handling

The current image-processing path does not yet provide a robust fallback for every image-access failure. A failed image operation can interfere with the reader reaching the speech stage.

The desired product behaviour should be:

```
Image fails
 ↓
Record/log failure
 ↓
Skip image or use approved fallback
 ↓
Continue reading webpage text
```

That behaviour should be verified by QA before it is described as implemented.

## Image order

The current implementation appends generated image descriptions after the main extracted text. It does not reconstruct the exact DOM reading order.

!!! warning
    Image descriptions are currently not guaranteed to be spoken at the position where the corresponding image appears on the page.

## Accuracy evaluation

A formal numerical AI accuracy benchmark is **not confirmed** in the current project materials.

The team should evaluate:

- factual correctness;
- hallucination/invented-detail rate;
- usefulness to users;
- language correctness;
- latency;
- image-access failure rate;
- behaviour across different image origins.

The existing [Test Scenarios and Test Cases](https://docs.google.com/spreadsheets/d/1HZEHZXPVk12cdFQLBZztsD4yPVLhykx85_LrxtLIeB0/edit?gid=400157956#gid=400157956) and [Usability Testing](https://docs.google.com/document/d/1sHpzLYos9pYdKLo-ahYypCzHlPNVBYcdYV0ZHeFWc3g/edit?tab=t.0) should provide the supporting QA/user evidence.

## AI limitations

- Gemini Nano may be unavailable.
- Availability depends on Chrome/device support and model readiness.
- Some images cannot be accessed by the extension.
- AI output is not guaranteed to be perfect.
- A failed image operation can currently affect reading startup.
- Image descriptions are not currently inserted at exact DOM position.
- There is no confirmed numerical accuracy result.
- The current candidate-selection logic is basic.