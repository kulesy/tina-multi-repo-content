---
title: Testing Multi-Repo Support
date: 2026-04-09T12:00:00.000Z
author: Josh Berman
---

# Testing Multi-Repo Support

This post is here to test the multi-repo catalog manager changes in PR #3368.

## Key Test Cases

### Case 1: Single-repo push
Traditional setup where schema and content are in the same repo.

### Case 2: Generator push (no schema change)
When generator repo is pushed but schema hasn't changed.

### Case 3: Content repo push
When content repo is pushed - schema should be fetched from generator repo's main branch.

### Case 4: Generator push with content repo
When generator repo is pushed in a multi-repo setup - content should be cloned from content repo.

## Schema Freshness

The generator's **main branch** is always the source of truth for schema. Content branches are indexed against this schema.
