# Security Architecture and Privacy

## Cyber Security SAD

The team's dedicated cyber-security architecture work is documented in the [Cyber Security SAD on Miro](https://miro.com/app/board/uXjVHyBAoK0=/).

This is an important project reference for security architecture decisions. The technical documentation separates security controls that can be confirmed from the current extension source from broader controls defined in the security architecture.

!!! warning
Where the Cyber Security SAD describes a control that cannot be demonstrated from the supplied source or backend evidence, it must be treated as a design/reference item, not automatically as an implemented control.

## Security responsibilities by layer

| Layer            | Security responsibility                                                                                                                                        |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Chrome extension | Use only required browser permissions, protect session state, avoid exposing backend secrets, and keep supported local AI processing local.                    |
| Service worker   | Coordinate authenticated API requests and keep backend communication outside the UI where appropriate.                                                         |
| Backend API      | Authenticate users, validate requests, enforce server-side access controls, and protect backend data.                                                          |
| Database         | Store backend data according to the backend security model and database controls. Exact controls require backend verification.                                 |
| Local AI         | Process supported AI inputs through Chrome's built-in AI capability rather than sending image data to the SecureReader backend in the supplied implementation. |
| Metrics          | Send only supported metric payloads through the backend metrics endpoint.                                                                                      |

## Security evidence boundary

The Cyber Security SAD, backend implementation, API documentation, extension source, and deployment configuration should be reviewed together before making a security claim.

The following are **not confirmed** in the current extension materials:

- server-side encryption at rest;
- database encryption;
- secret-management infrastructure;
- exact token expiry/rotation policy;
- rate limiting;
- brute-force protection;
- server-side audit logging;
- data-retention periods;
- account deletion/data-erasure implementation;
- production network/security configuration.

## Local AI and privacy

The image-description feature uses Chrome's built-in AI capability. The extension does not send the image to the SecureReader backend for Gemini Nano processing in the supplied implementation. This is an important privacy boundary.

## Backend data

The backend is involved in:

- authentication;
- account operations;
- metrics.

The exact backend retention and storage policies are not established by the extension source.

## Permissions

The extension requests browser permissions including:

- `storage`
- `activeTab`
- `scripting`

and access required to communicate with the SecureReader backend.

The extension also uses webpage content-script access for its reading functionality.

## Authentication storage

The authentication session is stored in `chrome.storage.session`. The service worker uses the session token for authenticated requests.

## Secrets

No backend database secret or signing secret should be placed in the extension. The supplied source contains the public backend URL because the browser must know where to send API requests.

## What remains local

The supplied architecture keeps these activities local to the browser where the required browser APIs are available:

- webpage DOM extraction;
- speech synthesis;
- Gemini Nano image processing;
- reader settings.

## What can leave the browser

Backend communication can include:

- account/authentication information;
- supported metrics.

The supplied image-description implementation does not use the backend to process the image.

## Areas requiring backend verification

The following cannot be confidently documented from the extension source alone:

- backend encryption at rest;
- server-side log retention;
- database retention;
- account deletion policy;
- backend administrative access;
- token expiry policy;
- exact server-side authentication implementation.

These are not confirmed in the current project materials and should be verified in the backend repository/API/security documentation.

## Security references

- [Cyber Security SAD](https://miro.com/app/board/uXjVHyBAoK0=/)
- [SecureReader SAD](https://lucid.app/lucidchart/c82a2e14-a27e-40cd-9c57-6490bf73eae1/edit?invitationId=inv_c3bd121b-0e1f-433d-a1d3-6ac2f1ff2416&page=0_0#)
- [API Documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs)
- [ERD](https://docs.google.com/document/d/1bwScVpZCh8B_trL5izIKHlrFW-PT39U_f7wSsHbguFY/edit?tab=t.0#heading=h.6fxiynwr0aa5)
