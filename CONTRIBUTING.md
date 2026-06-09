# Contributing

Thanks for helping improve Kotlin by Example. This project is a set of small, annotated Kotlin programs written in plain Markdown. Each example teaches one topic and shows real program output.

## Filename convention

- Examples live in `examples/` and are named `examples/NN-slug.md`.
- `NN` is a two-digit, zero-padded number that determines ordering (e.g. `01`, `09`, `42`).
- `slug` is a short, lowercase, hyphen-separated description (e.g. `hello-world`, `null-safety`).
- Every example must be listed in the `README.md` index under the correct section, using its number and human-readable title.

## Per-example template

Each example file follows this structure:

```
# NN. Title

Intro sentence(s).

(kotlin fenced code block with a focused snippet)

Optional follow-up prose and more kotlin blocks.

Running it:

(unlabeled fenced block: `$ kotlin run` then the real output)

[← Prev](NN-prev-slug.md) | [Index](../README.md) | [Next →](NN-next-slug.md)
```

## Style rules

- Keep snippets small and focused. Show just enough code to make the point.
- Prefer the standard library over third-party dependencies.
- Write idiomatic Kotlin that reflects current best practices.
- Show real program output. Run the example and paste the actual result; do not invent output.
- One concept per code block. Split unrelated ideas into separate blocks with prose between them.
- The first example omits the `← Prev` navigation link; the last example omits the `Next →` link. Every example keeps the `Index` link.
