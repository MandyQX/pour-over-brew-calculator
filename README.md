# Pour Over Brew Calculator

A single-page pour-over timer and recipe calculator. Enter a coffee dose, choose a brew method, and the app calculates total water, per-pour grams, cumulative targets, and step timing.

## Features

- Adjustable coffee dose and brew ratio
- Built-in recipes for Classic V60, 4:6 Method, James Hoffmann V60 One Cup, and One Bloom, Two Pours
- Per-step timer with start, pause, next-step, and reset controls
- Editable pour step names, durations, and water percentages
- Custom recipe copies saved in the browser
- Shareable recipe links for moving a recipe to another device
- Automatic rounding so the final pour lands exactly on the target water amount
- Responsive layout for desktop and mobile screens

## Quick Start

No install or build step is required.

1. Open `index.html` in a modern browser.
2. Enter your coffee dose in grams.
3. Adjust the water ratio if needed.
4. Choose a recipe from the Method dropdown.
5. Press Start and follow the active pour target.

## Using The App

The target water is calculated as:

```text
coffee dose x water ratio = total brew water
```

Each recipe step uses a percentage of the total brew water. The app rounds each pour to whole grams and adjusts the final positive pour so the total matches the target exactly.

The timer shows:

- Current elapsed brew time
- Active step name and note
- Current pour amount
- Total target water
- Total recipe time
- Current cumulative water target

## Custom Recipes

Use **Save as custom** to copy the current recipe. Custom recipes can be renamed and edited from the pour step editor.

For each step, you can edit:

- Step name
- Duration in seconds
- Water percentage

Use **Add** to add a new pour step. Use the `x` button beside a step to remove it. At least one step must remain in a recipe.

## Sharing Recipes

Use **Copy recipe link** to create a link for the currently selected recipe and coffee dose.

Send that link to another device and open it there. The app will import the shared recipe, select it, and save it in that device's browser.

This works on static hosting such as GitHub Pages because the recipe data is stored directly in the link. It is not automatic cloud sync: edits made later on one device will not appear on another device until you copy and open a new recipe link.

## Data Storage

Recipes and the current coffee dose are saved in the browser with `localStorage` under the key:

```text
pour-over-tool-state-v1
```

This means saved recipes stay on the same device and browser. They are not synced or uploaded anywhere unless you use a shareable recipe link.

Use **Reset defaults** to clear saved browser data and restore the built-in recipes.

## Project Structure

```text
.
|-- index.html   # App markup, styles, and JavaScript
`-- README.md    # Project documentation
```

## Development

The app is intentionally dependency-free. Edit `index.html`, then refresh the browser to test changes.

The JavaScript uses modern browser APIs such as `structuredClone()` and `Array.prototype.at()`, so it is intended for current desktop and mobile browsers.

## Current Limitations

- Custom recipes are saved only in the current browser.
- Step notes are shown in the timer, but the editor currently changes only step name, duration, and water percentage.
- Share links copy one recipe at a time and do not provide live cross-device sync.
