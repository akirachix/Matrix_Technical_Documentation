# Overview

## What SecureReader does

SecureReader is a Chrome extension designed to help people access and understand webpage content through accessibility-focused reading features.

The core experience is audio-based. SecureReader identifies readable content on the current webpage, processes that content into a reading sequence, and uses the browser's speech-synthesis capability to read it aloud.

SecureReader also contains an image-description feature. When Chrome's built-in AI is available, the extension can provide an image to the browser's local `LanguageModel` capability and request a concise description. The description is then added to the reading sequence and spoken.

The extension also contains user settings, authentication/account functionality, backend communication, usage metrics, and a content-purification capability intended for supported comments.

## Problem

A webpage is not only made of text. Important information can be communicated through images, diagrams, charts, illustrations, and other visual content.

A person listening to a page may therefore hear the text while missing information that is visible but not represented in the page's readable text.

SecureReader's image-description feature is intended to reduce that gap by turning suitable webpage images into spoken descriptions.

For the original product problem and solution research, see the [Problem and Solution Research](https://docs.google.com/presentation/d/1aoW5dxqPRSnOgqgC-Zd-hHDyUUPBEWXMJgV4vBmwBqg/edit?slide=id.g3e76be32d27_2_75#slide=id.g3e76be32d27_2_75).

## Users

SecureReader is intended for:

- people who benefit from hearing webpage content instead of reading it visually;
- people with visual accessibility needs;
- people who prefer listening to webpage content;
- users who need additional access to information contained in webpage images.

The product's stakeholder-facing presentation is available on our [Informational Website](https://matrix-informational-website-4wyi.vercel.app/).

## Main features

| Feature              | Current status                            | What it does                                                                                                  |
| -------------------- | ----------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Webpage reading      | Implemented                               | Extracts readable webpage text and speaks it.                                                                 |
| Language detection   | Implemented                               | Determines the likely webpage language for reading.                                                           |
| Voice selection      | Implemented                               | Selects an available browser voice matching the language where possible.                                      |
| Speech settings      | Implemented                               | Controls speed, volume, and voice profile.                                                                    |
| Image descriptions   | Partially implemented                     | Uses Chrome built-in AI/Gemini Nano to describe images.                                                       |
| User settings        | Implemented                               | Stores reader settings locally in Chrome storage.                                                             |
| Authentication       | Partially implemented                     | Signup, login, session handling, and account operations exist, with known gaps.                               |
| Metrics              | Partially implemented                     | Sends selected allowlisted usage metrics to the backend.                                                      |
| Comment purification | Partially implemented / known scope issue | Toxicity classification exists, but current reader behaviour is broader than the intended comment-only scope. |
| Voice commands       | Partially implemented                     | Supporting recognition/classification modules exist, but the full runtime flow is not connected.              |

## What SecureReader is not

SecureReader is not:

- a general webpage-cleaning service;
- a remote Gemini image-processing API;
- a payment platform;
- a cloud AI image service;
- a system that guarantees perfect AI image descriptions.
