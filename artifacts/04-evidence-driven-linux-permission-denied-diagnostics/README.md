# Evidence-Driven Linux Permission Denied Diagnostics

## Overview

This artifact demonstrates a structured approach
to diagnosing and fixing basic Linux
`Permission Denied` problems.

The objective is to prove the cause of an access
failure before changing permissions or ownership,
apply the minimum required fix, and verify that
access is actually restored.

---

## Engineering Workflow

**SYMPTOM → EVIDENCE → CAUSE → MINIMAL FIX → VERIFICATION**

A `Permission Denied` error is treated as a symptom,
not as a reason to immediately change permissions.

Evidence is collected first:

— `whoami` — identify the current user

— `id` / `groups` — identify group membership

— `ls -l` — inspect owner, group and `rwx`

The applicable access category is then determined:

**owner → group → others**

The required `r`, `w` or `x` permission is compared
with the actual permission in that category.

This identifies the specific access mismatch.

---

## Minimal Fix

The fix is selected according to the confirmed cause.

— `chmod` — when the required `rwx` permission
is missing

— `chown` — when ownership or group assignment
is the confirmed cause

Permissions are not broadened unnecessarily.

After the change, the new state is checked with
`ls -l`.

The original failed action is then repeated to
verify that access has actually been restored.

---

## Verification

A changed permission state does not by itself
prove that the original problem is solved.

The complete verification is:

**FIX → VERIFY STATE → RETRY ORIGINAL ACTION → VERIFY ACCESS**

The task is complete only when both the expected
permission state and the original access are
confirmed.

---

## Skills Demonstrated

— identifying the user and group context

— reading Linux owner, group and `rwx` permissions

— determining the applicable access category

— connecting a required action to `r`, `w` or `x`

— identifying a specific permission mismatch

— selecting `chmod` or `chown` from confirmed evidence

— applying a minimal access fix

— verifying state and retrying the original action

---

## Engineering Principle

**Do not fix `Permission Denied` by guessing.**

The workflow used here follows a simple rule:

**collect evidence → prove the cause → change only
what is necessary → verify the resulting state →
retry and prove that access is restored**