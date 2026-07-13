# Artifact 02

# Evidence-Driven Linux File Diagnostics

## Overview

This artifact demonstrates a practical workflow for
finding configuration files, log files and
relevant system information in Linux.

The focus is not on fixing problems.

The focus is on collecting evidence before making
engineering decisions.

---

## Engineering Idea

Linux diagnostics starts by locating the correct
files and collecting evidence before making
any changes.

The workflow combines file discovery and
content search into one repeatable process.

Evidence is collected first.

Only then can a hypothesis be checked.

---

## Evidence-First Workflow

```text
Symptom
↓

Evidence
↓

Hypothesis
↓

Check
↓

Verify
```

This workflow was consistently used during
practice and review.

---

## Skills Demonstrated

— navigating the Linux filesystem

— locating configuration files

— locating relevant log files

— viewing configuration files safely

— viewing large log files with `less`

— finding files by name

— searching text inside files

— combining `find` and `grep`

— following an evidence-first workflow

---

## Linux Commands Practiced

— pwd

— cd

— ls

— cat

— less

— find

— grep

— mkdir

— touch

— cp

— mv

— rm

— echo

— history

---

## Practice Scenarios

Practice included:

— locating configuration files

— locating relevant log files

— searching for specific messages inside logs

— viewing configuration and log files

— creating backup copies before changes

— creating a practice Linux directory structure

— working through the complete workflow
using Ubuntu Server over SSH

---

## Engineering Conclusions

Searching for files and searching inside files
are two parts of the same diagnostic workflow.

Correct evidence should be collected before
attempting any system changes.

Linux file structure provides the starting point
for collecting diagnostic evidence.

---

## Result

This artifact confirms practical experience with
a Linux file search and evidence collection
workflow required for Junior Hosting Support /
Linux Support roles.

The demonstrated workflow is based on
finding evidence before making decisions.