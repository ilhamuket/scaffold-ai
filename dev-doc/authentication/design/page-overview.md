# Authentication Pages Overview

**Date Created:** 2026-04-07
**Last Updated:** YYYY-MM-DD

---

## Page Summary

Authentication page group contains all user login, signup, password management, and verification flows.

---

## Pages in This Group

### 1. Login Page
**Folder:** `authentication/login/`
**Purpose:** Allow existing users to sign in to their account
**Key Sections:**
- Form (email/username + password input)
- Error states (invalid credentials, account locked)
- Links (forgot password, signup)
- Loading states

**Components Used:**
- Text Input (email/username)
- Password Input
- Submit Button
- Links
- Error Messages
- Loading Indicator

### 2. Signup Page
**Folder:** `authentication/signup/`
**Purpose:** Allow new users to create an account
**Key Sections:**
- Form (email, password, confirm password)
- Validation feedback
- Terms acceptance
- Loading states

### 3. Password Reset
**Folder:** `authentication/password-reset/`
**Purpose:** Allow users to reset forgotten passwords
**Flow:**
1. Email entry form
2. Confirmation (email sent)
3. Password reset form
4. Success confirmation

### 4. Email Verification
**Folder:** `authentication/email-verification/`
**Purpose:** Verify user email address
**Flow:**
1. Verification code entry
2. Resend code option
3. Success confirmation

## Navigation Flow

```text
Entry Point
    |
    +-- Login Page
        |
        +-- Forgot Password -> Reset -> Success -> Dashboard
        |
        +-- Sign Up -> Verify Email -> Dashboard
```

## Subsections Breakdown

### Login Page Subsections
1. **form/** - Email/username + password fields, submit button
2. **error-states/** - Invalid credentials, account locked, network error
3. **links/** - Forgot password, signup, help

### Signup Page Subsections
1. **form/** - Email, password, confirm password, terms
2. **validation/** - Real-time validation feedback, password strength
3. **success/** - Verification email sent message

### Password Reset Subsections
1. **email-entry/** - Enter email form
2. **confirmation/** - Email sent confirmation
3. **reset-form/** - New password entry
4. **success/** - Password reset successful

### Email Verification Subsections
1. **code-entry/** - Verification code input
2. **resend/** - Resend code link/button
3. **success/** - Email verified confirmation

## Related Documents

- `../prd.md` - Requirements for authentication
- `../userflow.md` - User flows for login/signup/reset
- `../../../guardrails/design/DESIGN_PROCESS.md` - Design process guide
- `../../../templates/design_spec_template.md` - Design spec template
