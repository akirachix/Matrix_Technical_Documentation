# Backend

## Backend purpose

The backend provides functionality used by the extension for:

- user registration;
- login;
- account/password operations;
- metrics.

## Backend URL

```
https://secure-reader-e8d40157a540.herokuapp.com
```

## API reference

The authoritative endpoint reference is the [SecureReader API documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs).

The API documentation should be used when a route, request schema, response schema, or authentication contract needs exact detail.

## Communication architecture

The popup does not need to own all backend communication. The current pattern is:

```
React Popup
 ↓
chrome.runtime message
 ↓
Service Worker
 ↓
fetch()
 ↓
SecureReader Backend
```

## Signup

The extension sends signup information including:

- first name;
- last name;
- email;
- password;
- password confirmation;
- location;
- user role.

The request is JSON encoded.

## Login

Login uses the backend's password-based authentication request. The extension submits:

- email/username;
- password;
- password grant.

The returned authentication/session information is stored for later authenticated requests.

## Authenticated request pattern

The extension sends authenticated backend requests through the service worker using a bearer token. A representative request pattern is:

```js
fetch(`${API_URL}/metrics`, {
  method: "POST",
  headers: {
    "Authorization": `Bearer ${token}`,
    "Content-Type": "application/json"
  },
  body: JSON.stringify(payload)
});
```

The service worker owns this backend communication rather than exposing database access directly to the browser.

## Bearer authentication

Authenticated requests use:

```
Authorization: Bearer <token>
```

The token/session is stored in `chrome.storage.session` under key `secureReaderSession`.

## API actions represented in the extension

| Operation | Route represented in extension | Status |
|---|---|---|
| Registration | `/registration/` | Implemented client request |
| Login | `/user/login` | Implemented client request |
| Forgot password | `/auth/forgot-password` | Implemented client request |
| Reset password | `/auth/reset-password` | Action exists; complete UI flow not confirmed |
| Change password | `/auth/change-password` | Implemented client request |
| Profile | `/auth/profile` | Implemented route mapping |
| Update profile | No matching service-worker action mapping confirmed | **Known issue** |
| Metrics | `/metrics` | Implemented client request |

The live API documentation remains authoritative if the backend has changed since the extension source was written.

## Known profile-update issue

The popup contains an `updateProfile` action. The service worker route/action mapping does not currently contain a matching `updateProfile` mapping.

This can result in:

```
Unsupported API action
```

This is a known integration defect.

## Error handling

The service worker uses `try/catch` around backend requests and returns error information to callers. The extension also uses `console.error` for failures.

A central production logging service is not confirmed in the supplied extension source.