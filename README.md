# Tina Multi-Repo Content

This repository contains the content (markdown files) for a multi-repo TinaCMS setup.

## Purpose

In a multi-repo setup:
- **Generator repo**: Contains the Tina schema and configuration
- **This repo (content)**: Contains the actual markdown content files

## Structure

```
content/
  posts/
    hello-world.md
    testing-multi-repo.md
    schema-workflow.md
```

## How It Works

When content is pushed to this repo:
1. TinaCloud webhook receives the push event
2. Event handler detects this is a content repo (`repoSource: 'content'`)
3. Schema is fetched from the **generator repo's main branch**
4. Content is cloned and indexed using that schema

## Schema Source

Content is **always** indexed against the generator repo's `main` branch schema, regardless of which content branch is being indexed. This ensures schema consistency.

## Testing PR #3368

This repo is set up to test the multi-repo catalog manager changes in https://github.com/tinacms/tinacloud/pull/3368

### Test Scenarios

1. **Content push**: Push to this repo should trigger indexing with generator schema
2. **Feature branch**: Create a feature branch and push - still uses generator `main` schema
3. **Force push**: Force push should trigger full reindex
