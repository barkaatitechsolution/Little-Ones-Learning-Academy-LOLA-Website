# Little One's Learning Academy (LOLA) — Official Website

The official landing page for the **Little One's Learning Academy (LOLA)** YouTube channel — a fun, playful website for kids and parents with educational videos, free printable PDFs, and one-click subscription to the channel.

🔗 Live preview: open `index.html` in any browser (static hosting only — works on **GitHub Pages**, **Netlify**, **Vercel**, or any static host).

---

## 📸 Preview

> 👉 Drop your screenshots into the `preview/` folder before pushing to GitHub:
> `preview/desktop.png` and `preview/mobile.png`.

| 🖥️ Desktop | 📱 Mobile |
|---|---|
| ![Desktop preview](preview/home.png) | ![Mobile preview](preview/mobile-home.png) |

---

## ✨ Features

### 🏠 Home Page (`index.html`)
- **Hero section** — channel branding, tagline, animated stats (subscribers, videos, views, rating) and big **Subscribe on YouTube** buttons.
- **"What We Learn"** section — pillars for ABCs & Phonics, Numbers & Counting, Colors & Art, and Songs & Social Skills.
- **Video showcase** — responsive video grid with lazy-loaded YouTube embeds (click the thumbnail to play, no slow page loads).
- **Free PDFs banner** — a compact call-to-action that links to the dedicated PDF library page.
- **Subscribe band** — a fun "join the LOLA family" section with benefit chips and subscribe button.
- **Parent testimonials** — social proof from happy families.
- **Floating subscribe button** — always-visible pill that bobs gently to draw attention.
- **Mobile drawer menu** — slides in from the right on phones, with backdrop and body-scroll lock.
- **Scroll-reveal animations** — sections fade in as you scroll.

### 📚 Free PDF Library (`pdfs.html`)
- **Resource grid** — beautiful cards for each free printable (Animal Chart, English Alphabet, Fruits, Numbers, Weather, Shapes & Colors). Cards are auto-generated from a config list — **add a PDF by copying one line**.
- **📥 Download from Google Drive** — one-click open of your shared Drive folder (or a per-file direct-download link when configured).
- **📨 Get by Email** — email capture modal that delivers the PDF straight to the subscriber's inbox via **EmailJS** (free, no server needed).
- **Error & success popups** — friendly toasts for:
  - ✅ Success — "PDF on its way!"
  - ⚠️ Invalid email address
  - 📭 EmailJS free-tier quota hit (200 emails/month → HTTP 429)
  - 😢 Generic sending failure
- **Escape to close** — modal closes with `Esc`, backdrop click, or the ✕ button.

### 🎨 Design & UX
- Bright, playful kid-friendly branding (yellow, teal, orange, pink).
- Rounded, cheerful typography (Baloo 2 + Fredoka from Google Fonts).
- Fully **responsive** — mobile, tablet, and desktop.
- Shared `styles.css` keeps both pages consistent.

---

## 🚀 Getting Started (Hosting)

Just upload these files together to your host:

```
📦 little-ones-learning-academy/
├── index.html      → Home page
├── pdfs.html       → Free PDF library
└── styles.css      → Shared styles
```

### GitHub Pages
1. Create a repo and upload these 3 files (keep the same folder layout).
2. Go to **Settings → Pages** → Source: **Deploy from a branch** → `main` / root.
3. Your site goes live at `https://<username>.github.io/<repo-name>/`.

---

## ⚙️ Configuration

### 1. YouTube channel & socials
In both `index.html` and `pdfs.html`, open the `CONFIG` section at the top of the `<script>`:

```js
const CHANNEL_URL   = "https://www.youtube.com/@LittleOnesLearningAcademy"; // your channel
const INSTAGRAM_URL = "https://www.instagram.com/your_handle";               // optional
const FACEBOOK_URL  = "https://www.facebook.com/your_page";                  // optional
```

### 2. Videos (home page)
Add your real YouTube **video IDs** (the part after `watch?v=`) to `VIDEO_IDS` in `index.html`, and update matching titles/descriptions in `VIDEO_META`. Cards with placeholder IDs automatically link to your channel instead.

### 3. Free PDFs (`pdfs.html`)
Edit the `RESOURCES` list:

```js
const RESOURCES = [
  {
    emoji: "🦁",
    name: "Animal Chart",
    file: "animal-chart.pdf",
    driveUrl: "",                                        // optional direct link
    url: "https://yoursite.com/pdfs/animal-chart.pdf",   // used by the email option
    desc: "Lions, elephants, monkeys and more."
  },
  // copy this block for every new PDF — the grid grows automatically
];
```

- **Drive folder** — the 📥 Download button opens your shared folder by default:
  ```js
  const DRIVE_FOLDER_URL = "https://drive.google.com/drive/folders/...";
  ```
- **Direct per-file link (optional)** — set `driveUrl` to force a direct download:
  ```js
  driveUrl: "https://drive.google.com/uc?export=download&id=FILE_ID"
  ```
- **Important:** the Drive folder/files must be shared **"Anyone with the link"** (Viewer).

### 4. Email delivery (EmailJS — free, 200 emails/month)
The "Get by Email" buttons send the PDF through [EmailJS](https://www.emailjs.com) with no server:

1. Create a free account at [emailjs.com](https://www.emailjs.com).
2. **Add an Email Service** (Gmail/Outlook) → copy its ID.
3. **Add an Email Template** with the variables `{{to_email}}`, `{{resource_name}}`, `{{resource_url}}` — link/attach the PDF in the template.
4. Copy your **Public Key** and paste all three into `pdfs.html`:

```js
const EMAILJS_SERVICE_ID = "YOUR_EMAILJS_SERVICE_ID";
const EMAILJS_TEMPLATE_ID = "YOUR_EMAILJS_TEMPLATE_ID";
const EMAILJS_PUBLIC_KEY  = "YOUR_EMAILJS_PUBLIC_KEY";
```

> 💡 The site gracefully handles the free tier's **200 emails/month** limit — visitors see a friendly "monthly limit reached" popup instead of a confusing error.

---

## 🛠️ Tech Stack

- **Plain HTML / CSS / JS** — no build tools, no frameworks, no dependencies beyond:
  - Google Fonts (Baloo 2, Fredoka)
  - EmailJS browser SDK (loaded from CDN)

---

## 📝 License

Made with ❤️ for little learners everywhere. Feel free to adapt and reuse for your own channel.
