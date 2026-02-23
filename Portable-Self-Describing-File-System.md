# Portable Self-Describing File System

**Version:** 1.1\
**Author:** Jakob Huggele\
**Date:** 2026-02-18\
**Status:** Final\
**License:** MIT Liense\
**Contact:** hello@jakobuggele.com

---

## Summary

Structurally self-sufficient hierarchical file system with AI-native, self-describing text files, now using stable unique IDs for each file.

---

# 1. Definition

## System Description

This system is a **structurally self-sufficient, hierarchical file architecture** composed of folders and self-describing files with unique IDs.

It exists to store structured information in a way that remains independent of host platforms, applications, or metadata systems.

It enables complete contextual understanding of stored material through:

* Explicit file identity
* Embedded meaning
* Direct file-to-file references using stable IDs

All files must be in **AI-native text formats**:

* `.md`
* `.txt`
* `.json`

No other file formats are allowed.

This ensures that content is fully readable and interpretable by AI systems without conversion or preprocessing.

The system is designed to be portable across operating systems, storage environments, and AI platforms without requiring structural adaptation to the host environment.

Meaning and relationships are encoded within files themselves using unique IDs, allowing the system to remain structurally self-sufficient even if human-readable file names change.

---

# 2. Structure

## 2.1 Hierarchy

The system is instantiated as a **folder tree**.

### Root Structure Example (using IDs)

```
root_folder/
├─ folder_1/
│   ├─ A1010_file_1.ai
│   └─ A1020_file_2.ai
├─ folder_2/
│   ├─ A2010_file_3.ai
│   └─ A2020_file_4.ai
```

### Hierarchy Rules

* Folders are used to organize files into logical groupings.
* Depth of hierarchy is unrestricted.
* Folder names represent structural grouping.
* The hierarchy provides navigation and containment only.
* IDs are stable identifiers for files.
* Human-readable file names may change, but the ID remains the primary reference for relationships.

---

## ID Naming Logic

* Format: `[Letter][Number][Number][Number]`
  Example: `A1010`, `A1020`, …, `A9090`, then `B1010`
* IDs leave space for future inserts without renumbering downstream
  Example: `A1011` can be inserted between `A1010` and `A1020`
* IDs are the only identifiers used in references between files.

---

## 2.2 File Anatomy

Every file in the system must contain the following components:

---

### 1. File ID

#### Purpose

The file ID serves as the stable, unique identifier for the file within the system.

#### Rules

* Must be included in the file’s Self-Description or header.
* Used in references instead of the human-readable file name.
* Never changes, even if the file name or folder changes.

---

### 2. Self-Description

#### Purpose

This section contains a textual summary of the file’s content and functions as embedded metadata.

#### Requirements

* Summarize the content of the file clearly and directly.
* Allow AI or human to understand the file’s content without accessing other files.

#### Example

```
ID: A1010

Self-Description:
This file documents the methodology and results of a specific intervention based on case-study A2010.
It details the actions taken, the observed outcomes, and the reasoning behind each step.
All information is textual and structured to be directly interpretable by an AI.
```

---

### 3. References (if applicable)

#### Purpose

Lists other files within the system that are directly relevant to this file using file IDs.

#### Rules

* References must use the unique IDs, not file names.
* Include only meaningful relationships.
* Indicates that the referenced file must be read to fully understand the context.

#### Example

```
References:
A2010
A2020
```

---

### 4. Content

#### Purpose

Contains the substantive material of the file, consistent with the Self-Description.

---

# Example File Structure

### File: `A1010_file_1.ai`

```
ID: A1010

Self-Description:
This file documents the methodology and results of a specific intervention based on case-study A2010.
It details the actions taken, the observed outcomes, and the reasoning behind each step.
All information is textual and structured to be directly interpretable by an AI.

References:
A2010
A2020

Content:
[Substantive material begins here.]
```

---

# 3. Operational Behavior

## When the Entire Folder Is Uploaded to an AI System

* The AI reads the folder hierarchy.
* The AI reads each file’s Self-Description and ID.
* The AI follows explicit references by ID where necessary.
* AI can build contextual understanding even if human-readable file names change.

---

## To Add a New File

1. Assign a new unique ID following the ID logic.
2. Create the file within the appropriate folder.
3. Write a complete Self-Description including the ID.
4. Add explicit references using IDs if the file depends on or relates to other files.
5. Add the substantive content.

---

## To Modify a File

* Update the Self-Description if its content changes.
* Update references by ID if relationships change.
* Ensure content remains consistent with the stated identity and scope.

---

# Conclusion

This document represents a fully self-contained, AI-native, text-only, structurally self-sufficient, self-describing, and replicable file system specification with stable unique file IDs for robust references.
