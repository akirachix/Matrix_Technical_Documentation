# Current Limitations, Known Issues, and Priorities

## Current Limitations and Known Issues

### Image access
Some visible webpage images cannot be accessed by the extension.

Known error: `The image cannot be accessed by the extension`

### Image error isolation
Image-processing errors can interfere with the reader's ability to reach speech.

### Image order
Image descriptions are not currently guaranteed to occur at the corresponding image's position in the reading sequence.

### Image candidate filtering
The current candidate logic is basic and does not fully distinguish meaningful images from every decorative or irrelevant image.

### Gemini Nano availability
The feature depends on browser/device/model availability.

### Purification scope
The current reader can classify webpage sentences, while the intended feature is supported-comment purification.

### Comment detector
`src/content/commentDetector.js` is not a complete implementation.

### Voice commands
Supporting command modules exist, but the full user-facing runtime flow is incomplete.

### Profile update
Popup and service-worker action mapping are inconsistent.

### Extension test automation
A dedicated automated extension test suite is not confirmed.

### Lint
The current codebase has lint failures.

---

## Current Development Priorities

### Priority 1 — Make image description reliable

The current technical priority is to make image descriptions dependable enough for the normal reader flow.

**Required improvements:**

- Handle inaccessible images without crashing the reader.
- Continue reading text when an image fails.
- Define and implement a safe image fallback.
- Improve image candidate filtering.
- Improve image placement in the reading sequence.
- Test image access across different origins and page types.
- Establish measurable AI evaluation criteria.

### Priority 2 — Correct comment purification scope

Move purification from general extracted sentences to supported-comment detection/classification.

The product rule is: **purify supported social media comments.**

### Priority 3 — Fix account integration

Resolve the profile-update action mismatch and verify the complete account flows.

### Priority 4 — Complete or clearly scope voice commands

Either connect the existing command modules to the reader runtime or explicitly keep the capability marked as partial/future.

### Priority 5 — Improve automated testing

Use the existing test scenarios as behavioural requirements for a future automated extension test suite.

### Priority 6 — Resolve lint issues

Bring the extension to a clean lint state or document intentionally accepted exceptions.