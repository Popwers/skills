# Interface Details Reference

Use this reference when a UI already works but still feels rough, flat, jumpy, or slightly off. These heuristics are distilled from the source article and translated into implementation guidance.

## Contents

1. Text wrapping
2. Concentric border radius
3. Contextual icon animation
4. Crisp text rendering
5. Tabular numbers
6. Interruptible animations
7. Split and stagger enter animations
8. Subtle exit animations
9. Optical alignment
10. Shadows instead of borders
11. Image outlines

## 1. Text wrapping

Use `text-wrap: balance` for headings or short blocks that would otherwise leave an orphaned last word.

Prefer this for:
- marketing headings
- card titles
- modal titles
- short explanatory copy

Use `text-wrap: pretty` only when you want a similar effect and the extra cost is acceptable.

```css
.balanced-title {
	text-wrap: balance;
}
```

Do not apply balancing blindly to long paragraphs.

## 2. Concentric border radius

When one rounded surface sits inside another, the radii should be concentric. A reliable default:

`outer radius = inner radius + padding`

Example:
- outer radius: `20px`
- inner radius: `12px`
- padding between them: `8px`

If inner and outer radii are arbitrarily matched, nested cards, inputs, and panels feel sloppy even when users cannot explain why.

Check this on:
- cards inside panels
- buttons inside rounded containers
- avatars or thumbnails inside rounded shells
- nested modals or sheets

## 3. Contextual icon animation

When an icon appears only in response to a state change, animate it instead of swapping it instantly. The best defaults are small changes to:
- `opacity`
- `scale`
- `filter: blur()`

This works well for:
- copy-to-clipboard confirmations
- save states
- success checks
- contextual action icons

Keep the motion short and tied to the interaction. The point is responsiveness, not spectacle.

## 4. Crisp text rendering

On macOS, light text can look heavier than intended. Applying font smoothing can make it appear thinner and cleaner.

```html
<body class="antialiased">
```

Or:

```css
html {
	-webkit-font-smoothing: antialiased;
}
```

Apply it at layout level rather than piecemeal so text rendering stays consistent across the app.

## 5. Tabular numbers

Use tabular numerals when numbers update or sit in columns and should not shift horizontally.

```css
.metric {
	font-variant-numeric: tabular-nums;
}
```

Useful for:
- dashboards
- counters
- timers
- invoices
- analytics tables
- animated KPIs

Watch out: some fonts change numeral style when tabular numerals are enabled.

## 6. Interruptible animations

For interactive UI, prefer transitions that can retarget when state changes mid-flight. Users often reverse intent before an animation finishes.

Rule of thumb:
- use transitions for interactive state changes
- use keyframes for one-off staged sequences

Good candidates for interruptible motion:
- dropdowns
- accordions
- drawers
- toggles
- hover state changes

If repeated clicks or rapid toggles make the UI feel stuck, the motion model is wrong even if the animation looks good in isolation.

## 7. Split and stagger enter animations

Do not animate a large block as one slab if it contains distinct pieces. Split meaningful chunks and stagger them lightly.

Typical enter stack:
- `opacity`
- `translateY`
- `blur`

Good split points:
- title
- description
- button row
- badge or eyebrow

Useful default delays:
- around `80ms` between words when splitting a title
- around `100ms` between larger sections

This creates more legibility and rhythm than animating the whole region at once.

## 8. Subtle exit animations

Exit motion should usually be softer than enter motion. Leaving elements do not need to demand equal attention.

Good pattern:
- stronger enter
- shorter, smaller exit

Instead of moving an element by its full height on exit, a small directional offset such as `-12px` often feels better while still signaling dismissal.

Keep:
- some motion
- some fade
- some blur if it matches the system

Avoid dramatic exits unless the product intentionally uses theatrical motion.

## 9. Optical alignment

When geometric centering looks wrong, trust the eye. Optical alignment is often necessary with icons, mixed shapes, or icon-plus-text controls.

Common fixes:
- slightly reduce padding on the icon side of a button
- add a tiny `margin` adjustment around an icon
- correct the icon artwork in the `svg` itself when possible

Check this on:
- play buttons
- chevrons
- asymmetrical logos
- circular icons beside text

Mathematically centered content can still look visually off-balance.

## 10. Shadows Instead Of Borders

For light surfaces, a subtle multi-layer shadow often feels better than a flat border because it adds separation and depth without looking harsh.

```css
.surface {
	box-shadow:
		0 0 0 1px rgba(0, 0, 0, 0.06),
		0 1px 2px -1px rgba(0, 0, 0, 0.06),
		0 2px 4px 0 rgba(0, 0, 0, 0.04);
}
```

On hover, darken the same shadow recipe slightly instead of swapping to a totally different effect.

This is especially useful when the background is:
- textured
- image-based
- multicolored
- not a flat solid designed for that exact border color

Transparent shadows adapt more gracefully than solid borders.

## 11. Image outlines

Images often benefit from a faint inner outline so they sit more cleanly in UI systems that otherwise use borders or surface separation.

```css
.image-outline {
	outline: 1px solid rgba(0, 0, 0, 0.1);
	outline-offset: -1px;
}

.dark .image-outline {
	outline-color: rgba(255, 255, 255, 0.1);
}
```

Use this for:
- avatars
- thumbnails
- screenshots
- media cards

The effect should be barely visible. It is there to define the edge and add depth, not to frame the image loudly.

## Review Order

If the user asks for an audit and time is limited, review in this sequence:

1. Text wrapping and tabular numerals
2. Optical alignment and border radius
3. Hover, enter, exit, and interruptibility
4. Shadows, borders, and image outlines

These are usually the fastest wins with the highest perceived payoff.
