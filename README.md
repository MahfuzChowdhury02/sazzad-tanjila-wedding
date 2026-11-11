# Sazzad & Tanjila — wedding invitation

A scroll-driven wedding invitation for **Sazzad Alam & Tanjila Nur**.

**Live site:** https://mahfuzchowdhury02.github.io/sazzad-tanjila-wedding/

| Event | Date | Venue |
|---|---|---|
| Wedding (Biye) | Friday, 4 December 2026 | Hall 24 Convention Center, beside MA Aziz Stadium, C.R.B. Road, Chattogram 4200 |
| Reception | Saturday, 5 December 2026 | City Hall Convention Center, Agrabad Access Road, Chattogram 4100 |

## What guests see

1. **The lane (hero).** An Old Dhaka lane turns from dusk to night under a crescent moon; the green shutters swing open and Sazzad and Tanjila lean out of facing windows. The Bismillah and their names fade in.
2. **Into her window.** The camera pushes into the bride's window.
3. **The envelope.** Her hennaed hands break the wax seal and lift the card. বিয়ের দাওয়াত, "Join us for our wedding celebration", a boat picture and the dates appear printed on that card.
4. **The boat ride.** The camera moves into the picture on the card and the boat ride begins; the Wedding card turns into the Reception card as you scroll.
5. **Two hearts, one promise.** The wedding stage at night with Surah Ar-Rum 30:21 in Arabic and English.
6. **The venues.** Map cards with "Get directions" (Google Maps) and "Add to calendar", and a countdown to the wedding day.

Everything in the hero moves with the scroll, forwards and backwards. A play/pause music button sits in the bottom-right corner.

## Folder layout

```
index.html                 the whole site (HTML, CSS and JS; no build step)
img/w/                     wide frames for computers and landscape tablets (2560×1440, AVIF, 2 frames per file)
img/t/                     portrait frames for phones (1080×1920, AVIF, 2 frames per file)
img/hi/                    full-resolution stills for the two camera moves (keeps zooms sharp)
img/card-photo*.webp       the picture printed on the card (wide and phone versions)
img/biye-stage.jpg         "Two hearts" background
img/hall.jpg               venues background
img/map.jpg                illustrated map artwork for the venue cards
music/                     background music
```

## How it works

- **Two frame sets.** The page picks the wide set or the phone set by screen shape. Phones get scenes recomposed for a tall screen, so both windows, the card and the boat stay in frame.
- **Drawn on canvas.** Each hero step is drawn on a `<canvas>` from the frame files, blending neighbouring frames so motion glides.
- **No waiting on decode.** Frames download once, then decode in the background outward from the reader's position (more eagerly ahead than behind), at the size the screen shows, within a memory budget (about 640 MB on computers, 260 MB on phones).
- **Sharp zooms.** The push into the window and the move into the card's picture are drawn from the full-resolution stills in `img/hi/`. The printed card text scales with the same zoom, so it stays on the card.

## Music

Browsers only allow sound after a visitor interacts with a page. The music starts on the first tap, click or key press anywhere (or immediately where the browser allows it), fades in and loops. The bottom-right button pauses and resumes it.

The current track, `music/wedding-instrumental.mp3`, is an original instrumental generated as a stand-in. To use the couple's chosen song, add an audio file you have the rights to (for example `music/pyaar-mein.mp3`) and change `MUSIC.file` in the script of `index.html`.

## Editing

All in the `<script>` near the bottom of `index.html`:

- **Names, dates, venues and map links:** the `EVENTS` list.
- **Countdown target:** `WEDDING_AT`.
- **Music file and volume:** `MUSIC`.

The couple's names in the hero and on the card are in the HTML of `index.html` (search for "Sazzad").

## Updating the live site

Commit and push to `main`. GitHub Pages republishes within a minute or two:

```bash
git add -A
```

```bash
git commit -m "Describe the change"
```

```bash
git push origin main
```

## Running locally

Serve the folder with any static server:

```bash
python -m http.server 8000
```

Then open http://localhost:8000.

## Still to add

- The couple's chosen song file (replacing the stand-in instrumental).
- Start times for the wedding and the reception (the countdown currently runs to midnight on 4 December).
- Parents' names.
- 4K frames for the boat ride on computers (currently 2K from a 1080p clip).

## Credits

Scenes, video clips, the map artwork and the stand-in music were generated with Higgsfield (GPT Image 2.6, Kling 3.0, Topaz upscaling, ElevenLabs Music).
