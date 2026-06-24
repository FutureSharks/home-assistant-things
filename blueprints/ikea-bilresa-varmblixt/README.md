# ikea-bilresa-varmblixt

This blueprint is for the Ikea Bilresa remote and Varmblixt matter over thread devices. It allows the Bilresa to control the Varmblixt as follows:

- Button 1 press: power on
- Button 1 long press: brightness up continuously while held, stops on release
- Button 1 double press: next colour
- Button 2 press: power off
- Button 2 long press: brightness down continuously while held, stops on release
- Button 2 double press: previous colour

## Configuration

| Input | Description | Default |
|---|---|---|
| Button 1 – Event Entity | Event entity for Button 1 | — |
| Button 2 – Event Entity | Event entity for Button 2 | — |
| VARMBLIXT Light | Light entity to control | — |
| Brightness Step (%) | How much brightness changes per repeat tick while held (1–20) | 5% |
| Repeat Delay (ms) | Time between each brightness step while held (100–1000 ms) | 300 ms |

## How continuous dimming works

When a `long_press` event fires, the automation enters a `repeat` loop (capped at 100 iterations as a safety net) that steps the brightness by the configured amount and then waits for the repeat delay. When you release the button the remote fires a `long_release` event, which triggers a new run of the automation. Because the automation runs in `restart` mode, the new run immediately cancels the looping run — stopping the dimming cleanly. The `long_release` branch itself has an empty sequence, so it does nothing other than kill the loop.
