# Sazzad & Tanjila — wedding invitation

A scroll-driven wedding invitation for **Sazzad Alam & Tanjila Nur**.

- **Wedding (Biye):** Friday, 4 December 2026 · Hall 24 Convention Center, C.R.B. Road, Chattogram
- **Reception:** Saturday, 5 December 2026 · City Hall Convention Center, Agrabad Access Road, Chattogram

## How it works

`index.html` is the whole site (no build step). The opening is one sticky hero that plays by scroll, forwards and backwards:

1. An Old Dhaka lane turns from dusk to night and the window shutters open.
2. The camera pushes into the bride's window.
3. She breaks the wax seal and lifts the card; the invitation is printed on it.
4. The camera moves into the boat picture on the card and the boat ride begins, with the wedding and reception dates.

Each step is drawn on a `<canvas>` from HD WebP frames in `img/f/` (`win-*`, `env-*`, `boat-*`), with neighbouring frames blended for smooth motion. Phones load every other frame to keep the download smaller.

## Editing

- Names, dates, venues and map links: the `EVENTS` list near the top of the `<script>` in `index.html`.
- Countdown target: `WEDDING_AT` in the same place.
- Parents' names and start times are not added yet.

## Running locally

Serve the folder with any static server, for example:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.

Images and video frames were generated with Higgsfield.
