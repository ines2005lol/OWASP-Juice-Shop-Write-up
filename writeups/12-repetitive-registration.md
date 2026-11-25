# Repetitive Registration

- **Difficulty:** ⭐
- **Category:** Improper Input Validation
- **Date solved:** 2026-11-26

## The goal

Follow the DRY principle while registering a user.

## Background

**DRY** stands for **"Don't Repeat Yourself"**, a programming principle. Here
it's a hint about the registration form, which asks you to type your password
twice ("Password" and "Repeat Password"). The challenge is to register
*without* repeating it correctly, meaning with two passwords that don't match.

Websites usually check form input in two places:

- **Client-side**, in the browser: fast feedback for the user, but the user
  controls the browser, so these checks can be changed or skipped.
- **Server-side**, on the backend: the real protection, because the user can't
  change it.

If a rule is only checked in the browser, it can be bypassed.

## What I did

### Step 1: Fill in the form with mismatched passwords

On the registration page I filled in the email, the security question and
answer, and the password fields, but typed **different** values in "Password"
and "Repeat Password". The form showed an error and the **Register** button
stayed greyed out.

### Step 2: Inspect the Register button

I right-clicked the Register button and opened it in DevTools' **Elements**
tab. The button has `id="registerButton"` and the attribute
**`disabled="true"`**. That's what stops it from being clicked: the browser's
own check decided the passwords don't match and disabled the button.

![Register button in the Elements tab with disabled="true"](../screenshots/12-repetitive-registration/disabled-button.png)

**What `disabled` does:** it's a standard HTML attribute for buttons and form
fields. When an element has it:

- it **can't be clicked** or selected with the keyboard
- it's shown **greyed out**
- a disabled button **can't submit** the form

It's a **boolean attribute**: what matters is whether it's there at all, not
its value. Even `disabled="false"` still disables the button. The only way to
enable it is to remove the attribute completely.

Juice Shop's frontend (Angular) adds `disabled` to the Register button while
the form is invalid, for example when the passwords don't match, and removes it
once the form is valid. It's purely a browser-side check: it changes how the
page behaves, but nothing stops a user from editing it. If you type in the form
again after removing it, Angular may add it back, so remove it right before
clicking.

### Step 3: Remove `disabled` and submit

I deleted the `disabled` attribute from the button in the Elements tab. The
button became clickable, I clicked **Register**, and the account was created
even though the two passwords were different. The challenge was solved.

## Why it works

The "passwords must match" rule is only enforced in the browser, by disabling
the button. The server never checks that the two passwords match. Once the
browser-side block was removed, the server accepted the registration as it
was.

## What I learned

- Anything in the browser (HTML attributes, disabled buttons, form checks)
  can be edited with DevTools.
- Client-side validation is for user convenience, not security.
- Every rule that matters must also be checked on the server.

## Remediation

**Vulnerability:** validation only done on the client side. Related to OWASP
Top 10 **A04: Insecure Design** (improper input validation).

How a developer should fix it:

1. **Validate on the server.** Check that the password and its confirmation
   match on the backend, and reject the request if they don't. The same goes
   for every other rule: required fields, length, format.
2. **Keep client-side checks only for user experience.** They're useful for
   instant feedback, but never rely on them for security.
3. **Test forms by bypassing the frontend**, for example by editing the HTML
   or sending requests directly, to make sure the server enforces every rule
   on its own.
