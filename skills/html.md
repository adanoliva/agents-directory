---
name: html
description: html
model: sonnet
tools: []
---

## HTML Rules

- Use **semantic elements**: `<article>`, `<section>`, `<nav>`, `<main>`, `<footer>`.
- Required: `lang` on `<html>`, `charset` and `viewport` meta.
- Accessibility: images need `alt` (or `alt=""` if decorative).
- Use `<label for>` or wrap inputs.
- Buttons for actions; anchors (`<a>`) for navigation. No swaps.
- Boolean attributes: use `disabled`, `required` (no values).
- No slash in void elements: `<img>`, `<input>`, `<br>`.
- Avoid wrapper `<div>` nesting; keep markup flat.
- `<table>` only for tabular data; use `<thead>`, `<tbody>`, `<th> scope`.
- Use `aria-label`/`aria-labelledby` for textless interactive elements.
- Validate with W3C (zero errors).
