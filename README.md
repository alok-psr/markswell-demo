# Markswell Education demo

Two website packages for the same local coaching centre are included in one React/Vite project:

- `/lite` — the ₹2k one-page package.
- `/pro` — the ₹3.5k multi-page package, with `/pro/classes`, `/pro/achievers`, `/pro/faculty`, `/pro/gallery`, and `/pro/contact`.

The root route (`/`) is a small demo-only package chooser.

## Run locally

```bash
npm install
npm run dev
```

Create a production build with `npm run build`. Preview it with `npm run preview`.

## Replace copy and data

All editable copy and structured content is in [src/data/content.js](src/data/content.js). Both site versions import the same file. The address and Maps listing have been supplied; the remaining programme, faculty, achievement, and contact details are temporary demo content.

Before launch, confirm or replace the temporary values in that file, including:

- teaching batches/timings;
- teacher name, bio, subjects, qualifications, and portrait;
- address, city/state/PIN, email, and map link;
- achiever names only with consent, their class/year/result/reflections, or remove cards that cannot be published;
- the optional FAQ guidance and gallery descriptions.

Review `index.html` too: its JSON-LD address reflects the supplied location. The phone numbers and centre name are taken from the supplied banner.

## Replace media

All media is local and can be swapped without changing code:

- `public/media/logo.png` — optional real logo slot. The interface intentionally renders a generic cap + text wordmark fallback, so it does not recreate a logo.
- `public/media/hero-classroom.webp` and `public/media/hero-classroom-mobile.webp` — responsive hero placeholders. They appear AI-generated and must be replaced with a photo of the client’s real classroom; confirm the replacement photo’s license before launch.
- `public/media/hero-poster.svg` — retained as a fallback for the gallery video; the hero itself uses the responsive classroom photos above.
- `public/media/hero-video.mp4` — add a muted, looping, licensed hero video under about 3 MB. The existing poster shows if it is absent or motion is reduced.
- `public/media/teacher.jpg` and `gallery-1.svg` through `gallery-4.svg` — replace with licensed centre/teacher photos.

The included SVGs are intentionally neutral placeholders, not stock imagery. When using Pexels/Unsplash or another source, download the permitted asset into this folder rather than hotlinking it. Do not use photos of minors in the achievers wall: it uses initials-only avatars by design.

To use another image extension, update the matching path in `src/data/content.js` (or the hero reference in `src/main.jsx`). Add the real `/public/media/logo.png` if the centre wants it; currently the fallback wordmark remains active.

## Deploy to Vercel

1. Push this project to a Git provider and import it into Vercel, or run `vercel` from the project folder.
2. Keep the default Vite build command (`npm run build`) and output directory (`dist`).
3. Deploy. [vercel.json](vercel.json) rewrites all requests to the React entry point, including direct visits to `/pro/contact`.

`public/_redirects` provides the equivalent SPA fallback for Netlify-style static hosts.

## Notes

- There is no backend. The enquiry form opens WhatsApp with the entered details prefilled.
- Google Fonts are loaded from Google; all photography/video assets are local placeholders.
- The footer marks the project as demo content until its placeholders are replaced.
