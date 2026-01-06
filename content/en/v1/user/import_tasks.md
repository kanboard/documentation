---
title: "Importing Tasks via CSV"
linktitle: "Import Tasks"
---

# Importing Tasks via CSV

Kanboard supports importing tasks from CSV files. This guide explains the CSV format, the positional field semantics used by the importer, and provides a recommended template for reliable imports.

## Overview

The CSV importer in Kanboard uses **positional fields**, not header names.  
This means the *order* of fields matters, and empty fields must be preserved to maintain alignment.

A minimal, stable header for task imports is:

reference,title,description,,,,column,,swimlane

The commas represent positional fields that must remain present, even when empty.

## Positional Field Reference

Kanboard interprets each row using the following positional mapping:

| Position | Meaning        | Notes |
|---------|----------------|-------|
| 1 | reference    | Optional identifier; can be anything |
| 2 | title        | Required; task title |
| 3 | description  | Optional; task description |
| 4 | category     | Leave empty unless using Kanboard categories |
| 5 | swimlane (ignored) | Fallback swimlane slot |
| 6 | column (ignored)   | Fallback column slot |
| 7 | column       | Primary column field; must match an existing board column |
| 8 | color        | Leave empty unless using Kanboard color codes |
| 9 | swimlane     | Primary swimlane field; must match an existing swimlane |

### Importer rule

Kanboard scans all fields left‑to‑right and assigns values based on pattern matching.  
The **last valid match wins** for each attribute.

Removing empty fields shifts the scan and changes how the importer interprets the row.

## Recommended Template Data Example

```csv
reference,title,description,,,,column,,swimlane
"task‑001","My task","Some description",,,,"Backlog",,"Your swimlane #1"
"task‑002","Another task","Some other description",,,,"Done",,"Your swimlane #2"
```

## Usage

1. Prepare a CSV file using the template above.  
2. Ensure column and swimlane names match your board exactly.  
3. Go to **Settings → Import Tasks**.  
4. Click **Choose File**
5. Click **Import** to upload the file and create your tasks.

## Troubleshooting

### Tasks appear in the wrong column or swimlane
One or more empty fields were removed, shifting positional alignment.

### Column or swimlane is ignored
The value does not match an existing Kanboard column or swimlane.

### Placeholder text disappears
Kanboard discards values that do not match known entities.

### Import succeeds but fields appear blank
Unused positional fields are ignored unless populated with valid values.
