# Page Reader

## Purpose

The page reader converts webpage content into a sequence that SecureReader can speak.

Main implementation: `src/content/reader.js`

## Selecting the readable root

The reader checks these selectors, in order:

1. `main`
2. `article`
3. `[role="main"]`
4. `body`

The first suitable element becomes the reading root.

## Cleaning webpage content

A clone of the root is cleaned before text extraction. The current implementation removes elements including:

- `script`
- `style`
- `noscript`
- `svg`
- `nav`
- `header`
- `footer`
- `form`
- `[aria-hidden="true"]`

The purpose is to reduce irrelevant content such as navigation, scripts, hidden elements, and decorative SVG content.

## Text extraction

The reader obtains text using `innerText`. Whitespace is normalised.

The current implementation limits extracted text to approximately **12,000 characters**. This is an implementation constraint and should not be presented as a universal webpage-size limit.

## Language detection

The reader checks language information from:

- HTML `lang`
- `Content-Language`
- language metadata
- `navigator.language`

The result is normalised to a browser-style language tag such as `en-US`.

## Sentence processing

The extracted text is divided into sentence-sized reading units. These units form the text portion of the reading sequence.

## Image processing

When image descriptions are enabled, image candidates are processed and generated descriptions are added to the reading sequence.

!!! note "Known limitation"
    The current implementation does not preserve the exact DOM position of each image in the final sequence.

## Purification interaction

The current reader can apply the Gemini Nano toxicity classifier to extracted sentences when purification is enabled.

!!! warning "Known scope issue"
    This is broader than the intended supported-comment-only requirement. See [Comment Content Purification](../ai/purification.md).