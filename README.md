# Bulb Watch

A phone stopwatch that watches a lightbulb through the camera. It checks the bulb on a timer (every minute by default) and stops the stopwatch when the bulb goes off.

## Use it

1. Open `index.html` on your phone over **https** (browsers only allow camera access on secure pages). The easiest way is GitHub Pages: in this repo, go to **Settings → Pages**, choose the `main` branch and the `/ (root)` folder, then open https://amchaiken-pixel.github.io/bulb-watch/.
2. Tap **Turn on camera** and allow camera access. Prop the phone up so it can see the bulb.
3. Tap the picture to put the box on the bulb.
4. With the bulb **on**, tap **Start stopwatch**. The first check learns what the lit bulb looks like.
5. Keep the screen on and the page open. Phones pause web pages in the background or with the screen locked. The page asks the phone to keep the screen awake.

When a check sees the bulb off, it looks again 3 seconds later (so a passing shadow doesn't count), then stops the stopwatch, beeps, vibrates, and shows when the bulb was last seen lit.

## How it decides

- **On the phone (default):** it measures how bright the boxed area is and compares that with the "on" brightness it learned at the start. The sensitivity slider sets the cutoff (default: stop below 50% of the "on" brightness). For tricky lighting, use **Learn "off" look** in Settings with the bulb switched off, and it will split the difference between the two.
- **Claude vision (optional):** paste an Anthropic API key in Settings and each check also sends a small snapshot to Claude, which decides whether the bulb is lit. If that call fails, the brightness reading is used instead. The key is saved only in your browser. Each check is one small API call, about 1,440 a day at the 1-minute interval.
