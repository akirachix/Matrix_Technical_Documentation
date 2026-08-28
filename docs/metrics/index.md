# Metrics and Monitoring

## Purpose

SecureReader contains a metrics layer for selected product usage events.

## Allowlisted metrics

The current service-worker allowlist contains:

- `image_described`
- `comment_purified`
- `voice_command_executed`

This limits which metric names can be submitted.

## Example payload

The extension sends data in the form:

```json
{
  "metric": "image_described",
  "count": 1
}
```

to `POST /metrics` using authenticated backend communication.

## Privacy boundary

The metric payload does not represent the webpage itself. The supplied extension implementation does not use metrics to send:

- webpage text;
- webpage comments;
- raw images;
- generated image descriptions;
- speech transcripts.

## Dashboard

The team has a [SecureReader Dashboard](https://matrix-dashboard-team-2dqrynx87-nagaba-shallot1.vercel.app/).

The exact server-side aggregation/storage implementation is not confirmed in the supplied extension materials.
