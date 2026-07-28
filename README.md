# LAKH Hostel – Website & Room Allotment Panel

A multi-page website for LAKH Hostel, combining a public marketing site with a simple admin panel for tracking room allotments. Built with vanilla HTML, CSS, and JavaScript — no frameworks, no backend, no build step.

**Live demo:** [lakhhotel.netlify.app](https://lakhhotel.netlify.app/)

## Features

**Public site (`index.html`)**
- Scrolling notice bar and responsive navbar with a mobile hamburger menu
- Hero section with a call-to-action to enquire
- Services grid (security, WiFi, canteen, electrical supply, furnished rooms, balcony)
- Photo gallery mixing local room images with hosted stock photos
- About section and guest testimonials
- Footer with contact details, sitemap links, and social profiles
- Smooth-scroll navigation to in-page sections

**User login (`Login.html`)**
- Front-end login form (email + password) with a "Remember Me" checkbox
- This is a demo form only — it does not authenticate against a backend; submitting shows a note explaining that

**Admin login (`Admin.html`)**
- Separate admin sign-in form (name, email, password)
- On submit, redirects to the room allotment panel (`Atten.html`) — this is a UI demo, not real authentication

**Room allotment panel (`Atten.html`)**
- Form to record student room allotments: date, student name, roll number, room number, and status (Allotted / Vacated)
- Entries are saved to the browser's `localStorage` and rendered in a table
- Each row has a "Remove" button to delete an entry
- Data persists across page reloads in the same browser, but is not shared between devices or synced anywhere

## Tech Stack

| Layer | Technology |
|---|---|
| Markup | HTML5 |
| Styling | CSS3 (separate stylesheet per page — see structure below), Google Fonts (Poppins) |
| Icons | [Font Awesome](https://fontawesome.com/) (via CDN, on the login pages) |
| Interactivity | Vanilla JavaScript (inline `<script>` blocks per page) |
| Data storage | Browser `localStorage` (room allotment records only — no server or database) |

## Project Structure

```
Hostel site/
├── index.html              # Public marketing site (home, services, gallery, about, contact)
├── Login.html               # Guest login form (front-end demo only)
├── Admin.html                # Admin login form → redirects to Atten.html
├── Atten.html                 # Room allotment panel (add/remove entries, stored in localStorage)
├── CSS/
│   ├── style.css              # Styles for index.html
│   ├── login.css               # Styles for Login.html
│   ├── admin.css                # Styles for Admin.html
│   └── Atten.css                 # Styles for Atten.html
└── src/
    ├── hostel.png               # Favicon / logo
    ├── hero.jpg                  # Hero background image
    ├── bg.jpg                     # Background image
    ├── security.jpg, wifi.jpg, canteen.jpg, electrical-supply.jpg,
    │   furniture.jpg, balcony.jpg # Service icons/images
    ├── room1.jpg – room4.jpg      # Gallery images
    └── bed.jpg                     # Additional asset
```

## Customization

- **Branding & content:** update the hostel name, address, contact details, and copy directly in `index.html`.
- **Services & gallery:** swap images in `src/` and update the corresponding `<img>` tags; the gallery currently mixes local images with two hardcoded Unsplash URLs, which you may want to replace with your own photos.
- **Testimonials:** edit or add `.testimonial-card` blocks in the `testimonials` section.
- **Room allotment data:** stored under the `lakhHostelAllotments` key in `localStorage`; clearing browser storage will reset it.
- **Real authentication:** both `Login.html` and `Admin.html` are UI-only. To make them functional, connect the forms to a real backend/auth service (e.g. Firebase Auth, a Node/Express API, or a serverless function) instead of the current `preventDefault()` handlers.

## Known Limitations

- **No real authentication.** Login and Admin forms accept any input and don't verify credentials against anything — they're front-end demos.
- **No shared backend.** Room allotment data lives only in the current browser's `localStorage`; it isn't visible from other devices or browsers, and clearing site data will erase it.
- **Mixed image sources.** The gallery pulls two images from Unsplash's CDN, so those specific images require an internet connection to load and are not bundled with the project.
- **Placeholder links.** FAQs, Hostel Rules, Privacy Policy, and "Forgot Password" links point to `#` and need real destinations.
