# Boomerang Text Thread Viewer

Boomerang parental controls export a child's texts as one flat, time-sorted CSV across
every contact — impossible to read as conversations. This is a single static page that
turns that export into a familiar messaging view: a contact list on the left, the
selected conversation on the right with incoming (left) and outgoing (right) bubbles.

**Everything runs in your browser.** The file is read locally and never uploaded — no
message leaves your device. The page makes zero network requests after it loads.

## Use it

1. Open `index.html` (locally by double-clicking it, or via your GitHub Pages URL).
2. Click **Choose a file** (or drag a CSV onto the box) and select a Boomerang export.
3. Pick a contact on the left to read the thread.

## What it does

- **Groups by contact**, normalizing phone-number variants (e.g. `+15555555555` and
  `15555555555`) so a person isn't split in two. Unnamed numbers show as the number.
- **Local time**, with day-separator dividers between dates.
- **Most-recent conversations first** in the contact list.
- **Media messages** (rows Boomerang captured with no text) show as
  `📎 <non-text content>` instead of an empty bubble.
- **Group-text hint:** a 👥 icon marks individual messages that look like they belong to
  a group chat. Hover it for the reason. See the limitation below.

## About group texts

The Boomerang export has **no concept of a group**: one phone number per row, no thread
ID, no recipient list. Group conversations are therefore scattered across the individual
contacts in the export, and they cannot be faithfully reconstructed. The 👥 icon is a
best-effort hint (it flags reactions that quote a message belonging to a different
contact, and messages that address multiple people), not a complete group view.

## Deploy to GitHub Pages (deploy from a branch)

No build step and no Actions workflow — GitHub serves `index.html` directly.

1. Push this repo to GitHub.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment → Source**, choose **Deploy from a branch**.
4. Select your branch (e.g. `main`) and folder **`/ (root)`**, then **Save**.
5. Wait ~1 minute, then open `https://<your-username>.github.io/<repo-name>/`.

## Privacy / committing

The `.gitignore` excludes `*.csv` so exports are never committed. Keep it that way — the
exports contain private message content. Only `index.html` needs to be published.

## License

[MIT](license)
