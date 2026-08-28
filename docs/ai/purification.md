# Comment Content Purification

## Product rule

Content purification is intended for **supported comments**, not general webpage content. This distinction must remain explicit throughout the product and documentation.

!!! danger
    SecureReader should not be described as a webpage-wide content purifier.

## Current implementation

The project contains a Gemini Nano toxicity classifier. The classifier uses categories such as:

- none
- low
- medium
- high

The current reader can skip text classified at higher toxicity levels when purification is enabled.

## Current scope problem

The current reader can classify extracted webpage sentences. The intended product scope is supported comments.

The file `src/content/commentDetector.js` does not currently provide a complete comment-detection implementation.

Therefore the end-to-end intended flow is not complete:

```
Detect supported comment
 ↓
Classify comment
 ↓
Filter only supported toxic comment
 ↓
Leave ordinary webpage content unchanged
```

## Status

**Partially implemented / Known scope issue.**

This should be corrected before the feature is described as a general production-ready comment-purification system.