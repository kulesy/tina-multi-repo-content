---
title: Understanding the Schema Workflow
date: 2026-04-09T18:00:00.000Z
author: Eli Kent
---

# Understanding the Schema Workflow

An important aspect of the multi-repo setup is understanding how schema changes work.

## The Workflow

1. **Schema changes happen in the generator repo**
   - Update `tina/config.ts` with new fields
   - Merge to `main` branch
   - This becomes the "deployed" schema

2. **Content changes happen in the content repo**
   - Content is always indexed against generator's `main` branch schema
   - Feature branches in content repo still use generator's `main` schema

## Important Constraint

You **cannot** test schema + content changes together in feature branches:

- If you add a new field to generator (feature branch)
- And add content using that field (content repo feature branch)
- The content indexing will **fail** because it uses generator's `main` schema

## Recommended Workflow

1. Merge schema changes to generator `main` first
2. Then create content that uses those new fields
3. This ensures content is always indexed with the correct schema
