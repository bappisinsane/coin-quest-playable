# Coin Quest — Playable Ad

A single-file interactive playable ad: an intro video, a tap-to-win chest
mechanic, and a jackpot end card. No build step, no dependencies, no network
calls.

## Run it

```bash
python -m http.server 8080
```

Then open <http://localhost:8080/>.

Opening `index.html` directly from disk also works, but serving over HTTP is
recommended — some browsers restrict video autoplay on a `file://` origin.

## How it plays

1. The intro video plays inside a 360x640 phone frame, with a skip button.
2. When the video ends, is skipped, or fails to autoplay, the playable UI
   fades in.
3. Tapping the chest (or the button) awards 1,000 gold, with a screen shake
   and a floating "+1,000 GOLD!" particle.
4. After three taps the jackpot end card appears — "You claimed 3,000 Gold
   Coins!" — with a download call to action.

## Files

```
index.html                  the whole ad: markup, styles and game logic
ad-video.mp4                intro video
Gemini_Generated_Image_*    background and hero art
```

## Implementation notes

- Vanilla HTML/CSS/JS; no framework, bundler or external requests.
- Fixed 360x640 stage, mobile-first, scaled to the viewport.
- The video-to-playable handoff has three entry paths: natural end, skip
  tap, and autoplay failure.
- The end-card CTA is currently a placeholder (`alert`); wire it to a real
  store URL before shipping.

## License

Not specified. Contact the author before reuse.
