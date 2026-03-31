# Permanent Link to Code Snippet Demo

This note mocks the GitHub UI for a permanent link to a code snippet.

> Based on the GitHub Docs, the real snippet card renders in GitHub comments in the same repository. In Markdown files like this one, GitHub treats the permalink as a normal URL instead of a rich code snippet.

<div style="max-width: 860px; margin-top: 16px; border: 1px solid #d0d7de; border-radius: 12px; overflow: hidden; background: #ffffff; box-shadow: 0 1px 3px rgba(27, 31, 36, 0.08); font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Helvetica, Arial, sans-serif;">
  <div style="display: flex; align-items: center; justify-content: space-between; gap: 12px; padding: 14px 16px; background: #f6f8fa; border-bottom: 1px solid #d8dee4;">
    <div style="display: flex; align-items: center; gap: 10px; min-width: 0;">
      <img src="https://github.githubassets.com/favicons/favicon.svg" alt="GitHub" width="18" height="18" />
      <strong style="font-size: 14px; color: #24292f;">src/utils/permalink.ts</strong>
      <span style="padding: 2px 8px; border: 1px solid #d0d7de; border-radius: 999px; font-size: 12px; color: #57606a;">L12-L19</span>
    </div>
    <span style="padding: 2px 8px; background: #ddf4ff; color: #0969da; border-radius: 999px; font-size: 12px; white-space: nowrap;">commit 8f3c2ab</span>
  </div>
  <div style="padding: 0; background: #f6f8fa;">
    <pre style="margin: 0; padding: 16px; overflow-x: auto; font-size: 13px; line-height: 1.6; color: #24292f; background: #f6f8fa;"><code><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">12</span><span style="background: #fff8c5;">export function copyPermalink(path: string, start: number, end?: number) {</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">13</span><span style="background: #fff8c5;">  const range = end ? `#L${start}-L${end}` : `#L${start}`;</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">14</span><span style="background: #fff8c5;">  return [</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">15</span><span style="background: #fff8c5;">    "https://github.com/acme/demo/blob/8f3c2ab",</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">16</span><span style="background: #fff8c5;">    path + range,</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">17</span><span style="background: #fff8c5;">  ].join("/");</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">18</span><span style="background: #fff8c5;">}</span></span><span style="display: block;"><span style="display: inline-block; width: 32px; color: #8c959f; user-select: none;">19</span></span></code></pre>
  </div>
  <div style="padding: 12px 16px; border-top: 1px solid #d8dee4; background: #ffffff;">
    <div style="margin-bottom: 8px; font-size: 12px; color: #57606a; text-transform: uppercase; letter-spacing: 0.04em;">Permalink</div>
    <code style="display: block; padding: 10px 12px; border-radius: 8px; background: #f6f8fa; border: 1px solid #d8dee4; font-size: 12px; color: #0969da; overflow-x: auto;">https://github.com/acme/demo/blob/8f3c2ab/src/utils/permalink.ts#L12-L18</code>
  </div>
</div>

## How it works on GitHub

1. Open a file or pull request diff.
2. Select one line or a line range.
3. Use the line menu and choose `Copy permalink`.
4. Paste that link into a comment to get the rich snippet UI.

## Markdown File Note

If you want to link to lines in a Markdown file on GitHub, use the file URL with `?plain=1`, then append `#L...`.

Example:

```text
https://github.com/<org>/<repo>/blob/<commit_SHA>/README.md?plain=1#L14
```
