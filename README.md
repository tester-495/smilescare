# SmileCare Dental Clinic — Website

A premium, fully responsive dental clinic website built with **React + Vite**.

## Tech stack

- React 19 + Vite
- Plain modern CSS (custom design tokens, no framework)
- No backend — the appointment form simulates a successful submission

## Getting started

```bash
npm install
npm run dev
```

Then open the local URL Vite prints (usually `http://localhost:5173`).

To build for production:

```bash
npm run build
npm run preview
```

## Project structure

```
src/
├── components/       # One component per section, plus shared UI (Icon, SmartImage)
├── data/              # Content arrays for services, doctors, testimonials, before/after
├── hooks/             # useReveal (scroll animations), useCountUp (animated stats)
├── App.jsx            # Assembles all sections in order
├── main.jsx           # React entry point
└── index.css          # Design tokens, resets, shared utility classes
```

# SmileCare Dental Clinic — Website

A premium, fully responsive dental clinic website built with **React + Vite**,
with a motion-and-interaction layer built on Framer Motion, Lenis and Swiper.

## Tech stack

- React 19 + Vite
- **Framer Motion** — scroll reveals, hero mouse-parallax, magnetic CTAs, mobile menu
- **Lenis** — buttery smooth scrolling + smooth anchor navigation
- **Swiper** — the testimonials carousel (centered active slide, autoplay, keyboard nav)
- Plain modern CSS (custom design tokens, no framework)
- No backend — the appointment form simulates a successful submission

## Getting started

```bash
npm install
npm run dev
```

Then open the local URL Vite prints (usually `http://localhost:5173`).

To build for production:

```bash
npm run build
npm run preview
```

## Project structure

```
src/
├── components/       # One component per section, plus shared UI
│   ├── Reveal.jsx        # Scroll-triggered reveal wrapper (Framer Motion)
│   ├── SmoothScroll.jsx  # Lenis smooth-scroll provider
│   ├── CustomCursor.jsx  # Desktop-only magnetic cursor (dot + ring)
│   └── MagneticButton.jsx# Pointer-attraction CTA wrapper
├── lib/
│   └── motion.js          # Centralized Framer Motion variants + timing tokens
├── data/              # Content arrays for services, doctors, testimonials, before/after
├── hooks/             # useCountUp (animated stats)
├── App.jsx            # Assembles all sections in order
├── main.jsx           # React entry point
└── index.css          # Design tokens, resets, shared utility classes
```

## Motion & interaction notes

- **Reduced motion**: every animated component (`Reveal`, `CustomCursor`,
  `MagneticButton`, `SmoothScroll`, the Hero parallax, stat counters) checks
  `prefers-reduced-motion` and falls back to a static, fully accessible
  rendering — no parallax, no cursor, no smooth-scroll hijacking.
- **Custom cursor & magnetic buttons** are automatically disabled on
  touch/coarse-pointer devices (`pointer: fine` + `hover: hover` media query),
  so mobile keeps its native, fully usable cursor and tap targets.
- **Hero parallax** uses layered `useTransform` depth (background → image →
  foreground cards) driven by pointer position, with spring easing so it
  never feels jittery.
- Only `transform`/`opacity` are animated for scroll reveals and hovers to
  keep everything on the compositor thread.

## Notes

- Images are pulled from Unsplash by URL. If any single image fails to load
  (e.g. offline environment), it gracefully falls back to a branded
  placeholder instead of a broken-image icon — see `SmartImage.jsx`.
- The appointment form validates name, email, phone, service, date and time
  client-side and shows a success state after a simulated delay. Wire up
  `handleSubmit` in `Appointment.jsx` to a real API when you're ready.
- The contact map is a styled placeholder with a working "Open in Google
  Maps" link — swap in Google Maps Embed or Mapbox when you have an API key.
- `index.html` includes Open Graph tags and `Dentist` JSON-LD structured
  data built only from the business details already in `Contact.jsx` — no
  invented ratings, awards, or review counts.

