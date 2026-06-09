# Login Page — Test Cases

A comprehensive set of test cases for a typical web login page (username/email +
password, with "Remember me", "Forgot password", and optional social/SSO login).

**Legend**
- **Type:** Functional · Validation · UI/UX · Security · Accessibility · Compatibility · Performance
- **Priority:** P1 (critical) · P2 (high) · P3 (medium) · P4 (low)
- **Result:** Pass / Fail / Blocked (fill in during execution)

---

## 1. Functional — Authentication

| ID | Title | Preconditions | Steps | Expected Result | Type | Priority |
|----|-------|---------------|-------|-----------------|------|----------|
| TC-001 | Login with valid credentials | Registered, active account | 1. Open login page 2. Enter valid username/email 3. Enter valid password 4. Click **Login** | User is authenticated and redirected to dashboard/home; session created | Functional | P1 |
| TC-002 | Login with valid email vs. valid username | Account allows both | Log in once with username, once with email | Both succeed (if supported) | Functional | P2 |
| TC-003 | Login with invalid password | Valid account | Enter valid username + wrong password → Login | Generic error "Invalid username or password"; user stays on page | Functional | P1 |
| TC-004 | Login with non-existent username | — | Enter unregistered username + any password | Same generic error (no account-existence leak) | Security | P1 |
| TC-005 | Login with empty username and password | — | Leave both empty → Login | Inline validation errors; no request sent | Validation | P1 |
| TC-006 | Login with empty username only | — | Password filled, username empty → Login | "Username is required" | Validation | P2 |
| TC-007 | Login with empty password only | — | Username filled, password empty → Login | "Password is required" | Validation | P2 |
| TC-008 | Login with leading/trailing spaces in username | Valid account | Enter " user " (padded) | Username trimmed and login succeeds (or clear error) | Functional | P3 |
| TC-009 | Password is case-sensitive | Valid account | Enter correct password with altered case | Login fails | Security | P2 |
| TC-010 | Username case-insensitivity | Per spec | Enter username in different case | Behaves per spec (usually case-insensitive) | Functional | P3 |
| TC-011 | Login for deactivated/suspended account | Suspended account | Valid credentials → Login | Blocked with appropriate message | Functional | P1 |
| TC-012 | Login for unverified email account | Unverified account | Valid credentials → Login | Prompt to verify email; login blocked or limited | Functional | P2 |
| TC-013 | Login redirects to originally requested page | Deep link requires auth | Hit protected URL → redirected to login → log in | Redirected back to originally requested page | Functional | P2 |

## 2. Functional — Remember Me & Sessions

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-020 | "Remember me" persists session | Log in with box checked, close & reopen browser | User stays logged in (persistent cookie within expiry) | Functional | P2 |
| TC-021 | Without "Remember me" session ends | Log in unchecked, close browser, reopen | User must log in again (session cookie cleared) | Functional | P2 |
| TC-022 | Logout invalidates session | Log in → Logout → press Back | User is not authenticated; redirected to login | Security | P1 |
| TC-023 | Session timeout / idle expiry | Log in, stay idle past timeout, act | Session expired; redirected to login | Security | P2 |
| TC-024 | Concurrent sessions policy | Log in on two browsers | Behaves per policy (allowed or older invalidated) | Functional | P3 |
| TC-025 | Already logged-in user opens login page | Authenticated user navigates to /login | Redirected to dashboard (or shows logged-in state) | Functional | P3 |

## 3. Validation — Input Fields

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-030 | Invalid email format | Enter "user@", "user", "user@@x" | "Enter a valid email" (if email field) | Validation | P2 |
| TC-031 | Max length enforcement | Enter very long username/password (e.g. 500+ chars) | Capped at max length or rejected gracefully; no crash | Validation | P2 |
| TC-032 | Min length feedback | Enter password shorter than min | Appropriate message (login still returns generic auth error) | Validation | P3 |
| TC-033 | Whitespace-only inputs | Enter only spaces | Treated as empty / required error | Validation | P2 |
| TC-034 | Special characters in password | Password with `!@#$%^&*()` etc. | Accepted; login works with correct special-char password | Validation | P2 |
| TC-035 | Unicode / emoji in fields | Enter unicode/emoji | Handled without error; correct encoding | Validation | P3 |
| TC-036 | Paste into password field | Paste a password | Paste allowed (unless intentionally blocked) | UI/UX | P3 |
| TC-037 | Autofill / browser password manager | Use saved credentials | Fields populate and login succeeds | UI/UX | P3 |

## 4. UI / UX

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-040 | Page layout renders correctly | Load page | Logo, fields, button, links visible and aligned | UI/UX | P2 |
| TC-041 | Show/hide password toggle | Click the eye/show icon | Password text toggles between masked and visible | UI/UX | P2 |
| TC-042 | Password masked by default | Type password | Characters shown as dots/asterisks | Security | P1 |
| TC-043 | Tab order is logical | Press Tab repeatedly | Focus moves username → password → remember → login → links | Accessibility | P2 |
| TC-044 | Submit via Enter key | Fill fields, press Enter | Form submits (same as clicking Login) | UI/UX | P2 |
| TC-045 | Loading/disabled state on submit | Click Login | Button shows loading and is disabled to prevent double submit | UI/UX | P2 |
| TC-046 | Error message styling | Trigger an error | Error is clearly visible (color/icon) and readable | UI/UX | P2 |
| TC-047 | Placeholder/label clarity | Inspect fields | Labels/placeholders clearly describe each field | UI/UX | P3 |
| TC-048 | Forgot password link works | Click "Forgot password?" | Navigates to password reset flow | Functional | P1 |
| TC-049 | Sign-up / register link works | Click "Create account" | Navigates to registration page | Functional | P2 |
| TC-050 | Field focus & error reset | Edit a field after an error | Stale error clears appropriately | UI/UX | P3 |

## 5. Security

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-060 | Account lockout after N failed attempts | Enter wrong password N times | Account temporarily locked / CAPTCHA / delay enforced | Security | P1 |
| TC-061 | Brute-force / rate limiting | Rapid repeated login attempts | Requests throttled or blocked | Security | P1 |
| TC-062 | SQL injection attempt | Enter `' OR '1'='1` in fields | Login fails; no injection; query parameterized | Security | P1 |
| TC-063 | XSS attempt in fields | Enter `<script>alert(1)</script>` | Input sanitized/escaped; no script executes | Security | P1 |
| TC-064 | Credentials sent over HTTPS | Inspect network during login | Request uses HTTPS/TLS; no plaintext credentials | Security | P1 |
| TC-065 | Password not in URL / not logged | Submit login, inspect URL & logs | Password sent in POST body, never in query string or logs | Security | P1 |
| TC-066 | No sensitive data in client storage | After login, inspect localStorage/cookies | No plaintext password; tokens are HttpOnly/Secure | Security | P1 |
| TC-067 | Generic error messages | Trigger various failures | Errors don't reveal whether username exists | Security | P2 |
| TC-068 | CSRF protection on login form | Inspect form submission | Anti-CSRF token present and validated | Security | P1 |
| TC-069 | Session token rotates after login | Compare session ID pre/post login | New session ID issued (prevents session fixation) | Security | P1 |
| TC-070 | Back button after logout | Logout → Back | Protected pages not served from cache; auth required | Security | P2 |
| TC-071 | CAPTCHA appears when triggered | Hit failed-attempt threshold | CAPTCHA shown and required to proceed | Security | P2 |
| TC-072 | MFA/2FA challenge (if enabled) | Log in to a 2FA-enabled account | Prompted for second factor; access only after success | Security | P1 |
| TC-073 | Expired/invalid token handling | Use stale auth token | Rejected; user re-authenticated | Security | P2 |

## 6. Forgot Password Flow (entry from login)

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-080 | Request reset with registered email | Forgot password → enter valid email | Reset email sent; generic confirmation shown | Functional | P1 |
| TC-081 | Request reset with unregistered email | Enter unknown email | Same generic confirmation (no existence leak) | Security | P2 |
| TC-082 | Reset link expiry | Use an old reset link | Expired link rejected with message | Security | P2 |
| TC-083 | Reset link single-use | Reuse a consumed reset link | Rejected | Security | P2 |

## 7. Social / SSO Login (if applicable)

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-090 | Login with Google/Apple/GitHub | Click provider button | OAuth flow completes; user logged in | Functional | P1 |
| TC-091 | Cancel SSO consent | Start SSO, cancel on provider | Returned to login; clear message; no session | Functional | P2 |
| TC-092 | SSO email maps to existing account | Use SSO with existing email | Linked/handled per policy | Functional | P2 |
| TC-093 | SSO provider error | Provider returns error | Graceful error message | Functional | P3 |

## 8. Accessibility (a11y)

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-100 | Screen reader labels | Navigate with screen reader | All fields/buttons announced with proper labels | Accessibility | P2 |
| TC-101 | Keyboard-only operation | Complete login using only keyboard | Fully operable; visible focus indicators | Accessibility | P2 |
| TC-102 | Color contrast | Check text/inputs/errors | Meets WCAG AA contrast ratios | Accessibility | P2 |
| TC-103 | Error association | Trigger field error | Error programmatically associated with field (aria-describedby) | Accessibility | P3 |
| TC-104 | Zoom / text resize | Zoom to 200% | Layout remains usable, no clipping | Accessibility | P3 |

## 9. Compatibility

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-110 | Cross-browser | Test on Chrome, Firefox, Safari, Edge | Consistent appearance and behavior | Compatibility | P2 |
| TC-111 | Responsive / mobile layout | View on phone & tablet widths | Layout adapts; controls usable | Compatibility | P2 |
| TC-112 | Mobile keyboard types | Focus email vs password on mobile | Appropriate keyboard (email keyboard for email field) | Compatibility | P3 |
| TC-113 | Orientation change | Rotate device | Layout reflows correctly | Compatibility | P3 |

## 10. Performance & Reliability

| ID | Title | Steps | Expected Result | Type | Priority |
|----|-------|-------|-----------------|------|----------|
| TC-120 | Page load time | Load login page | Loads within acceptable threshold (e.g. < 2s) | Performance | P3 |
| TC-121 | Login response time | Submit valid login | Auth completes within acceptable threshold | Performance | P3 |
| TC-122 | Double-click submit | Rapidly double-click Login | Only one request processed; no duplicate sessions | Functional | P2 |
| TC-123 | Network failure during login | Disable network, submit | Friendly error; no app crash; retry possible | Functional | P2 |
| TC-124 | Server 500 during login | Force server error | Graceful error message; no stack trace exposed | Security | P2 |
| TC-125 | Slow network behavior | Throttle network | Loading indicator shown; no premature timeout | Performance | P3 |

---

## Notes
- Replace generic field names with your app's actual fields, URLs, thresholds,
  and lockout/timeout values.
- Remove sections that don't apply (e.g. SSO, MFA, CAPTCHA) and add
  product-specific flows as needed.
- Map each P1 case into your automated regression suite first.
