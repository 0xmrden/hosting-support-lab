# Evidence-Driven Linux Package Management

## Overview

This artifact demonstrates a basic evidence-driven
approach to Linux package management.

The objective is to determine the current package
state before making changes, perform only the
required action, and independently verify the result.

---

## Engineering Workflow

TASK  
↓  
EVIDENCE  
↓  
DECISION  
↓  
MINIMAL ACTION  
↓  
VERIFY

Package-management commands are selected according
to the engineering question being answered.

— `apt search <package>` — identify the package

— `apt policy <package>` — compare installed and
available versions

— `dpkg -l <package>` — verify package state

— `<program> --version` — verify program version

A system change is performed only after the
available evidence shows that it is required.

---

## Package Management Decisions

Installation:

— `sudo apt install <package>`

Update decision:

— `sudo apt update`

— `apt policy <package>`

— `sudo apt install --only-upgrade <package>`

Removal while preserving package-managed
configuration:

— `sudo apt remove <package>`

Removal together with package-managed
configuration:

— `sudo apt purge <package>`

Each state-changing operation is followed by
an independent verification of the resulting
package state.

---

## Basic APT Troubleshooting

An APT error is treated as a symptom rather than
an instruction to immediately modify the system.

SYMPTOM  
↓  
EVIDENCE  
↓  
CAUSE  
↓  
MINIMAL FIX  
↓  
RETRY  
↓  
VERIFY

The workflow was applied to basic cases involving:

— an incorrect or unavailable package name

— stale local package information

— broken dependencies

For dependency problems confirmed by APT evidence:

— `sudo apt --fix-broken install`

The original failed operation is then repeated
before the final state is verified.

---

## Practical Verification with nginx

The workflow was applied to the `nginx` package.

Commands used:

— `apt search nginx`

— `sudo apt update`

— `apt policy nginx`

— `sudo apt install nginx`

— `dpkg -l nginx`

— `nginx -v`

`dpkg -l nginx` provides evidence of the package
state.

`nginx -v` independently confirms the installed
program version.

Service management, nginx configuration, HTTP,
ports and logs are outside the scope of this
artifact.

---

## Skills Demonstrated

— Linux package discovery and installation

— package state and version verification

— installed versus available version comparison

— evidence-based update decisions

— `remove` versus `purge` selection

— basic APT troubleshooting

— independent verification after system changes

---

## Engineering Principle

**Successful command execution does not equal
verified system state.**

The package-management workflow used here follows
a simple rule:

**collect evidence → make a decision → perform the
minimum required change → verify the resulting state**