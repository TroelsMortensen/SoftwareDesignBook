# Software Architecture Book

A practical, teaching-focused book on software architecture, design, architectural styles, patterns, testing, and related engineering topics.

This repository contains source materials, examples, and a shared domain case study used across chapters and classroom sessions.

## Why this project exists

This book is built from real teaching practice.
Its goal is to connect core theory with concrete examples that can be used in class, mentoring, and software projects.

Topics include:

- software architecture fundamentals
- architecture and design principles
- architectural styles
- design patterns
- quality attributes and trade-offs
- testing strategies across levels

## Core case study

The canonical domain reference for examples is:

- `Case.md` - **Project "Abyssal Watch"** (Deep Sea Kaiju Exploration case study)

This document defines:

- ubiquitous language and glossary rules
- baseline entity catalog and relationships
- business invariants
- lifecycle and state flows
- reusable scenarios for architecture and pattern examples

Use it as the naming and modeling source of truth across chapters.

## Repository structure (high level)

- `main.tex` - main LaTeX entry point
- `parts/` - chapter and section content
- `parts/architectural-styles/` - architectural style chapters
- `out/` - generated artifacts (for example `main.pdf`)
- `Case.md` - shared domain baseline for examples

## Intended audience

- software engineering students
- practicing developers moving into architecture roles
- technical leads and architects
- instructors teaching architecture and design

## Working approach

This book emphasizes:

- clear, consistent domain language
- incremental depth per chapter
- examples that stay coherent across topics
- balancing conceptual rigor with practical applicability

## Build notes

The manuscript is LaTeX-based.
Use your preferred LaTeX toolchain/editor workflow to compile `main.tex` into PDF output.

## Status

Work in progress. Content evolves continuously as chapters are expanded, refined, and aligned with teaching material.

## License

Add your preferred license here (for example, MIT, CC BY-NC, or All Rights Reserved).
