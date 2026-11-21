# How to add a field note

1. Write the note in Markdown and save it as `posts/<slug>.md`. The slug is the short name in the link, for example `power-analysis-basics`. Use lowercase letters, numbers and hyphens only.
2. Add one entry to `posts/posts.json`:

```json
{
  "slug": "power-analysis-basics",
  "title": "What a power trace actually shows",
  "date": "2026-12-01",
  "summary": "One or two sentences shown on the home page and under the title.",
  "tags": ["hardware", "side-channel"],
  "minutes": 6
}
```

Put a comma between entries. `tags` and `minutes` are optional. Newest date shows first.

Supported Markdown: `##` and `###` headings, paragraphs, bullet and numbered lists, `>` quotes, code fences, inline code, bold, italic, links and images (`![alt](images/name.png)`, with the image file in `posts/images/`).
The first `# Title` line in the file is dropped because the title comes from `posts.json`.
