# Bulb Watch

A stopwatch that watches a small green LED through the camera. It checks the LED on a timer (every minute by default) and stops the stopwatch when the LED goes off.

Live page: https://amchaiken-pixel.github.io/bulb-watch/

## Use it

1. Open the page over **https** on a phone or iPad (browsers only allow the camera on secure pages).
2. Tap **Turn on camera**, allow access, and prop the device so it sees the LED. Tap the picture to put the small box right over the LED.
3. **Quick test (the default):** with the LED on, tap **Learn LED ON**. Switch it off and tap **Learn LED OFF**.
4. **Confirm:** switch the LED on and off again. The "Detected now" box must follow it. Once the app has seen both states read correctly, tap **It matches — continue**.
5. Switch the LED on and tap **Start stopwatch**. It refuses to start if the LED looks off. Prefer to skip the test? Tap **Skip the test** to use a default switch point instead.
6. Keep the screen on and the page open. The page asks the device to stay awake.

When a check sees the LED off, it looks again 3 seconds later (so a passing shadow doesn't count), then stops the stopwatch, beeps, and shows when the LED was last seen lit.

## How it decides

It measures how much green light is in the box: how far the green channel sticks out above red and blue, averaged over the greenest few percent of pixels. Red lights, white lamps and grey areas score near zero. The quick test records the "on" and "off" scores, and the line between them is the switch point (50% by default; change it in Settings). Moving or resizing the box means redoing the test.

Optional: paste an Anthropic API key in Settings and each check also sends a small snapshot to Claude to decide whether the LED is lit. The key is stored only in your browser.
