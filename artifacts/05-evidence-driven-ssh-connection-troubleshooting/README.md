# Evidence-Driven SSH Connection Troubleshooting

## Overview

This artifact demonstrates an evidence-driven approach to diagnosing basic SSH connection and authentication problems.

The workflow was practiced using a physical Dell server running Debian 13.

The objective is to identify the failure stage, investigate the available evidence, apply a justified correction, and independently verify remote access.

---

## Engineering Workflow

**SYMPTOM → EVIDENCE → HYPOTHESIS → CHECK → ACTION → VERIFY**

SSH access involves separate stages:

**TARGET → CONNECTION → SERVER IDENTIFICATION → AUTHENTICATION → REMOTE SHELL → VERIFICATION**

An SSH error can identify the stage of failure without proving its exact cause.

Changes to authentication or configuration must follow evidence, not assumptions.

---

## Diagnosing SSH Failures

Initial connection:

`ssh <user>@<host>`

Detailed client-side diagnostics:

`ssh -v <user>@<host>`

Failure categories covered during training:

- `Could not resolve hostname` — target resolution
- `Connection timed out` / `Connection refused` — connection stage
- `REMOTE HOST IDENTIFICATION HAS CHANGED!` — server identification
- `Permission denied` — user authentication

These messages guide investigation rather than prescribe automatic fixes.

A changed server host key must be verified before it is trusted.

---

## Authentication and SSH Keys

Practical exercises included password authentication, SSH key generation, manual public-key installation, and authentication troubleshooting.

Key principles:

- The private key remains on the client.
- The public key is authorized for the intended remote user through `~/.ssh/authorized_keys`.
- Server host keys and user authentication keys serve different purposes.

Commands and checks:

- `ssh-keygen` — generate an SSH key pair
- `ls -l ~/.ssh/` — inspect SSH files on Linux
- `ssh <user>@<host>` — attempt remote authentication
- `ssh -v <user>@<host>` — examine authentication evidence

Public-key installation was practiced manually from a Windows client to the Debian server.

Successful authentication must be verified independently of key-file presence.

---

## Remote Access Verification

After authentication, the remote session is checked:

- `whoami` — confirm the remote user
- `hostname` — confirm the remote system
- `exit` — close the remote session

**CONNECTION SUCCESS ≠ VERIFIED REMOTE ACCESS**

Verification confirms that the expected user has obtained a shell on the intended system.

---

## Skills Demonstrated

- SSH connection and remote shell verification
- identifying connection and authentication failure stages
- interpreting basic SSH client errors
- collecting diagnostic evidence with `ssh -v`
- password and public-key authentication
- SSH key generation and public-key installation
- troubleshooting basic authentication failures
- verifying the remote user and system
- evidence-driven troubleshooting and verification

---

## Engineering Principle

**An SSH error identifies a failure stage, not necessarily its root cause.**

**Collect evidence → test the hypothesis → apply the minimum justified action → independently verify remote access.**