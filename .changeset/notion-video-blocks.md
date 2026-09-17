---
"blume": patch
---

Import video blocks from Notion pages. A video block previously rendered as an `unsupported Notion block` comment, so neither uploaded videos nor pasted YouTube links appeared in the output. A YouTube link now becomes a `<YouTube>` embed, and any other video becomes a `<video>` player whose source is downloaded at build time — Notion's uploaded-file URLs are signed and expire, so they would otherwise rot the build. Downloads stream to disk through a shared concurrency gate with a timeout, a file already on disk is reused instead of fetched again, an extension-less asset is named by the response's media type, and a video link that answers with a web page (a Vimeo or Loom URL) is reported as a warning rather than written out as a broken player. String props the adapter writes (captions, toggle titles) use JSX expression form, so a double quote in a Notion caption no longer breaks the page.
