---
id: YYYY-MM-DD-short-slug
title: "Original title, in its original language"
authors: []
type: article | paper | book | book-chapter | video | podcast | transcript | report | note | email
role: primary | verification
verifies: []          # if role is verification — which claim(s) it was fetched for
url:
archived_from:        # for web sources: the address downloaded from, or the archive copy
retrieved: YYYY-MM-DD # for web sources: when the content was fetched
published: YYYY-MM-DD
ingested: YYYY-MM-DD
language:
checksum:
domain: [DOMAIN]
original_file: original.pdf
locator_scheme: page | heading | timestamp | none
---

# Source metadata

This file lives in `raw/<id>/` and is the identity record of the raw source. Once a source enters `raw/`, neither this file nor `original.*` is modified (any change requires explicit approval).

The `authors` field above is bibliographic — it records the **third-party author of the source**, which is exactly what a citation needs.

## Provenance

Where the source came from and in what context it landed in `inbox/`. If `role: verification`: which claim it was fetched to check, and why this source was chosen (primacy, publisher, date).

## Wiki counterpart

Summary page: `wiki/sources/<id>.md`

## Locators

How claims point into this document: page numbers for PDF (`#page=N`), heading anchors for markdown, timestamps for video or audio. If no locator scheme is possible, record why (e.g. scan without OCR, unpaginated stream).

## Notes

Technical notes about the raw file: was OCR needed, are pages missing, what is in `assets/`, was the download partial.
