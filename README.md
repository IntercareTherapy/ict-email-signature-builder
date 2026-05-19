# Intercare Email Signature Installer

A self-contained, single-file web tool that lets Intercare Therapy staff generate and install a branded Outlook email signature in under 30 seconds — no IT involvement required.

---

## What it does

- Presents a live form where staff enter their name, job title, phone, and email
- Renders a real-time preview of the branded signature
- Copies the formatted signature to the clipboard (rich HTML, ready to paste into Outlook)
- Offers a `.htm` file download as a fallback for browsers that block rich clipboard access
- Includes step-by-step Outlook installation instructions for Windows, Mac, Web, and mobile

The Intercare logo, brand colors, HQ address, and legal disclaimer are baked directly into the file — staff only fill in their personal details.

---

## Usage

1. Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari)
2. Fill in your details in the left panel — the preview updates live
3. Click **Copy signature**
4. Open Outlook and go to your signature settings (see in-app instructions for your platform)
5. Create a new signature, paste, and save

> **If Copy signature doesn't work:** Click **Download .htm file**, open the downloaded file in a browser, press `Ctrl`/`Cmd` + `A` to select all, then `Ctrl`/`Cmd` + `C` to copy, and paste into Outlook.

---

## Deployment

This is a **single static HTML file** with no dependencies, no build step, and no server required.

### Hosting options

| Option | Steps |
|---|---|
| **GitHub Pages** | Push `index.html` to the repo → enable Pages in Settings → share the URL |
| **Vercel / Netlify** | Connect the repo → auto-deploys on every push to `main` |
| **Internal file share** | Drop `index.html` on a shared drive — staff can open it directly |
| **Email it** | Attach `index.html` and staff open it locally in their browser |

### Recommended: GitHub Pages

1. In the GitHub repo, go to **Settings → Pages**
2. Set source to **Deploy from a branch**, branch: `main`, folder: `/ (root)`
3. Save — GitHub will provide a URL like `https://your-org.github.io/repo-name/`
4. Share that URL with staff

---

## Customization

All editable content is inside `index.html`. No build tools needed — open the file in a text editor.

| What to change | Where to find it |
|---|---|
| Default field values (name, title, phone, email) | `<input>` tags with `id="f-name"`, `f-title`, `f-phone`, `f-email` |
| HQ address | The `<!-- Headquarters -->` section inside `<script type="text/html" id="sig-template">` |
| Logo | The `<img src="data:image/png;base64,..."` inside the sig template — replace the base64 string with a new encoded image |
| Brand colors | CSS variables at the top of the `<style>` block: `--navy`, `--teal`, `--cream`, etc. |
| Legal disclaimer | The `<p>` tag at the bottom of the sig template containing "WARNING:" |
| HQ move ribbon | The `New HQ` `<td>` row at the bottom of the sig template — remove when no longer needed |

---

## Browser support

| Browser | Copy signature | Download .htm |
|---|---|---|
| Chrome 76+ | ✅ | ✅ |
| Edge 79+ | ✅ | ✅ |
| Firefox | ⚠️ May be blocked (use Download) | ✅ |
| Safari 13.1+ | ✅ | ✅ |

The app uses the [Clipboard API](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API) with an `execCommand` fallback. If both are blocked, the Download option always works.

---

## File structure

```
index.html          ← The entire app (HTML + CSS + JS, self-contained)
README.md           ← This file
```

No `node_modules`, no build output, no config files needed.

---

## Contributing

1. Create a feature branch: `git checkout -b feature/your-change`
2. Make your edits to `index.html`
3. Test by opening the file locally in a browser
4. Open a pull request to `main`

Avoid committing directly to `main`.

---

## Maintained by

Intercare Therapy · Brand & Communications  
501 Shatto Place, Los Angeles, CA 90020  
[intercaretherapy.com](https://www.intercaretherapy.com)
