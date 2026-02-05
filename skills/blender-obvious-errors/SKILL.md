---
name: blender-obvious-errors
description: Evidence-first troubleshooting for obvious Blender crashes, startup failures, missing external files, add-on conflicts, and common mesh/UV/color-management issues. Use when a user reports a Blender error/warning or "Blender is broken" behavior and you must propose the most obvious checks first, strictly grounded in official Blender Manual documentation (include doc URLs in Markdown).
---

# Blender Obvious Errors

## Purpose

Diagnose and resolve the most obvious Blender problems first, without guessing, and using only official Blender documentation as authority.

This skill is intentionally narrow: it focuses on evidence collection, common misconfigurations, and "first checks" that people often skip.

## Scope boundary (non-goals)

- Do not provide art direction, aesthetics feedback, or modeling “taste” opinions.
- Do not present folklore fixes as facts. If the manual does not support a claim, say the docs are silent or ambiguous and stop there.

## Hard rules

- Always separate **Confirmed** (user-provided evidence) from **Inferred** (hypothesis + what evidence would confirm/refute it).
- Treat missing information as data: if you cannot proceed, say exactly what is missing, why it matters, and what to provide next.
- Every proposed check or fix must include at least one official Blender Manual URL in Markdown.
- Prefer `https://docs.blender.org/manual/en/latest/...` links when available.
- If behavior depends on Blender version, ask for the user’s version first. If you must assume, state the assumption explicitly and link to the relevant versioned docs.

Official link index: `references/blender-manual-urls.md`.

## Minimum diagnosis intake (ask if missing)

Ask for: Blender version, operating system, what operation triggered the problem, exact error text (copy/paste), and whether it reproduces after restarting Blender.

If the issue is a crash or startup failure, also ask whether the user can reproduce it with factory settings and with add-ons disabled.

## Obvious-first workflow

### 1) Get evidence before theorizing

If the user reports an error dialog, request the exact text (copy/paste) plus a screenshot if available.

If the user reports a crash, startup failure, or render failure, request console/log output first (System Console and/or command line), and cite the official command line / crash docs from `references/blender-manual-urls.md`.

### 2) Classify the symptom into a known bucket

Pick the smallest bucket that matches the evidence:

- Startup / crash / won’t launch
- Missing external files (textures, HDRIs, caches, etc.)
- Missing linked libraries / placeholders
- Mesh integrity problems (non-manifold, normals)
- UVs / texture mapping clearly incorrect
- Render looks different across machines (color management)
- Add-on conflict / preferences corruption

### 3) Propose the most obvious checks first (with docs)

For the selected bucket, propose 1–3 checks in priority order. For each check:

- Explain why it matches the symptom (based on evidence)
- Include at least one official Blender manual URL in Markdown
- If it’s a hypothesis, label it **Inferred** and say what evidence would confirm it

If the docs do not clearly support a fix, stop and say the docs are silent/ambiguous.

## Repo learning rule (pattern note)

When an issue is resolved, output a short “pattern note” suitable for committing to the repo (e.g., `docs/blender/error-playbook.md`). Keep it short and structured so it’s easy to paste.

Template:

```md
### Symptom
…

### Root cause
…

### Minimal reproduction
…

### Fix
…

### Official docs
- …
```
