engine.css - Universal Utility Engine
engine.css is a low-level CSS utility engine built around a math-based variable system.
It gives you full control over spacing, layout, sizing, position, borders, flex/grid gaps, transforms, and responsive behavior - without bloating your stylesheet.

Unlike giant frameworks (Tailwind, Bootstrap), engine.css is:

- Minimal (one engine, small presets)
- Extendable (add only what you need)
- Predictable (1 unit = 1px unless modified)
- Responsive with max-width breakpoints
- Design-system friendly
- Readable and maintainable
You build as you go, not upfront.


--------------------------------------

Why engine.css exists
Traditional CSS becomes messy because you keep:

- rewriting the same rules
- scattering styles across files
- fighting specificity
- checking “where the hell did I style this before?”
- adding CSS for every component
Utility-first systems solve that - but existing ones are huge and rigid.

engine.css is the opposite:

- 1 central engine
- 20–30 preset values
- Add custom values when needed
- Zero bloat
- Zero lock-in
It's a portable CSS operating system, not a framework.

--------------------------------------

Core Principle
Class sets variable → Engine interprets → CSS applies

Example:

<div class="mt-40 px-24 radius-8"></div>

Values come from variables:
.mt-40 { --mt: 40; }
.px-24 { --px: 24; }
.radius-8 { --radius: 8; }

Engine converts units → pixels:
[class*="mt-"] { margin-top: calc(var(--unit) \* var(--mt, 0)); }

This means:

- You NEVER write margin-top manually.
- You NEVER repeat properties.
- You NEVER fight specificity.
- You only add values when you need them.

--------------------------------------

Mental Model
Write values only when needed.

Not:
.pt-1
.pt-2
.pt-3
...

Instead:
.pt-32 { --pt: 32; } /_ only because you needed 32px _/

This keeps your stylesheet tiny.

--The engine handles the logic. Your classes only supply the numbers.--

--------------------------------------

Included Utility Categories
Engine supports these out of the box:

- Margin (mt, mb, ml, mr, mx, my)
- Padding (pt, pb, pl, pr, px, py, p)
- Width / Height (w, h, minw, maxw, minh, maxh)
- Borders (bw-)
- Border radius (radius-)
- Flex/grid gaps (gap-, rowgap-, colgap-)
- Position offsets (top-, bottom-, left-, right-, insetx-, insety-)
- Z-index (z-)
- Opacity (0–100 → 0–1)
- Scale (percentage → transform)
- Rotate (degrees)
- Display helpers
- Flex alignment helpers
- Position helpers

--------------------------------------

Responsive System (Max-Width)

Breakpoints:
Prefix     Max Width
xxl:       ≤1999px
xl:        ≤1440px
lg:        ≤1299px
md:        ≤1024px
sm:        ≤860px
xs:        ≤599px


Usage:
<div class="mt-40 lg:mt-24 sm:mt-12"></div>

Each breakpoint overrides the variable - not the CSS property - which keeps your stylesheet clean.

--------------------------------------

How to Extend engine.css
Add a new spacing value:
.mt-88 { --mt: 88; }

Add a new padding size:
.pb-60 { --pb: 60; }

Add a new width:
.w-640 { --w: 640; }

Add a custom breakpoint override:
@media (max-width: 1299px) {
.lg:pb-60 { --pb: 60; }
}

That’s it.

No searching for files.
No rewriting components.
No inheritance issues.
No CSS fights.

--------------------------------------

How to Use It in WordPress

Works perfectly with:

- Elementor
- Bricks
- Oxygen
- Gutenberg
- ACF Blocks
- Custom Themes
You simply add classes inside HTML blocks or component HTML.

Because engine.css avoids specificity, it never breaks themes.

You can drop it into:
/wp-content/themes/your-theme/assets/css/engine.css

Then enqueue via:
wp_enqueue_style('engine', get_template_directory_uri() . '/assets/css/engine.css', [], false);

Everything works.

--------------------------------------

Why Developers Understand It Easily

- Class names follow natural naming (mt-40, gap-24)
- Units are always predictable (1 unit = 1px)
- Utilities are consistent across all categories
- Responsive overrides look like Tailwind
- The file is readable and modular
- No learning curve beyond basic CSS knowledge
A junior can pick it up in minutes.
A senior will appreciate its simplicity.

--------------------------------------

When to Add Custom Utilities

Do NOT pre-generate 1–500 values.

Add values only when the design requires it.

Your stylesheet will remain tiny and powerful.

--------------------------------------

Why engine.css is future-proof

- Based on native CSS variables
- No build step
- No compilation
- Framework-agnostic
- Works everywhere (HTML, React, WordPress, PHP templates)
- Can be tree-shaken manually
- Easy to migrate or expand
It’s not dependent on any tooling.


