# Waybar Microphone Control — Design and Styling Report

## Visual direction

The microphone control follows the Waybar's existing cyberpunk/neon language: a nearly black translucent panel, compact rectangular geometry, cyan highlights, yellow status warnings, and restrained outer glows. It is designed as part of the bar rather than as a visually separate widget.

## Design tokens

The control reuses the shared palette defined in `style.css`:

| Role | Token | Value |
|---|---|---|
| Bar and icon contrast | `@void` | `#000000` |
| Module surface | `@panel` | `rgba(0, 0, 0, 0.88)` |
| Active/accent state | `@cyan` | `#55ead4` |
| Muted state | `@yellow` | `#f3e600` |
| Default foreground | `@white` | `#ffffff` |

Cyan communicates that the microphone is active. Yellow makes the muted state immediately distinguishable without using the red reserved for urgent and critical conditions.

## Shape and spacing

The microphone inherits the common neon module shell:

- `4px 2px` outer margin
- `26px` minimum height
- `2px` corner radius
- `1px` semi-transparent cyan border
- Black panel surface at 88% opacity
- Subtle cyan shadow at rest

The microphone then uses `2px 7px` padding and a `16px` minimum content width. This gives both microphone states the same stable footprint and visually centers their glyphs without changing the dimensions of surrounding modules.

## Typography and iconography

Icons use the bar's existing font stack:

```css
font-family: "0xProto Nerd Font", "Symbols Nerd Font";
font-size: 13px;
font-weight: bold;
```

The state icons are:

- Active: ``
- Muted: `󰍭`

The original muted glyph, ``, was replaced because its diagonal slash creates asymmetric visual weight and appeared off-center despite mathematically balanced padding. The replacement has more suitable Nerd Font metrics for the compact square button.

## State styling

### Active

The active microphone uses cyan foreground on the dark panel. Its border and low-intensity cyan glow come from the shared module shell, keeping the state bright but not distracting.

```css
#custom-microphone.active {
    color: @cyan;
}
```

### Muted

The muted microphone uses yellow for the glyph and border, with a slightly stronger yellow glow. This changes three visual signals at once—icon, color, and border—so the state remains recognizable at a glance.

```css
#custom-microphone.muted {
    color: @yellow;
    border-color: @yellow;
    box-shadow: 0 0 5px alpha(@yellow, 0.45);
}
```

### Hover

Hover uses a solid cyan fill, cyan border, and stronger cyan glow:

```css
background-color: @cyan;
border-color: @cyan;
box-shadow: 0 0 8px alpha(@cyan, 0.8);
```

The foreground becomes black to maintain clear contrast against bright cyan and yellow surfaces. This rule applies consistently across the bar's interactive modules, including muted, charging, disconnected, privacy, workspace, media, and power states.

The black foreground override is placed at the end of the stylesheet. This is an intentional cascade decision: state classes such as `.muted` can have the same specificity as `:hover`, so the final hover rule ensures state colors never override hover contrast.

## Design principles followed

1. **Consistency:** reuse the established palette, dimensions, border, radius, and glow instead of creating a one-off button.
2. **State clarity:** combine icon and color changes so mute status does not depend on color alone.
3. **Visual stability:** keep a fixed content width so switching state does not resize the module or shift neighboring content.
4. **Optical alignment:** choose glyphs by their perceived visual center, not only their nominal font dimensions.
5. **Contrast:** use black foreground content whenever the hover surface becomes bright.
6. **Restrained emphasis:** reserve the strongest glow for interaction while keeping the resting state subtle.

## Styling acceptance criteria

- Both microphone icons appear optically centered inside an identically sized button.
- Active state is cyan; muted state is yellow.
- The module matches the height, border, radius, surface, and glow of adjacent neon modules.
- Hovering produces a bright fill with clearly legible black foreground content.
- State-specific colors do not override the black hover foreground.
- Toggling state does not resize the button or move neighboring modules.
