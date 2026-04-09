# Design System: Kasim Aslam — Delegation Masterclass Landing Page

## 1. Visual Theme & Atmosphere
A premium, dark editorial interface with cinematic confidence. The atmosphere is intense and direct — like a high-stakes boardroom presentation shot in a film noir. Deep charcoal backgrounds, surgical gold accents, and editorial typography command authority without noise. Density is low-to-medium, giving each section room to breathe and land with impact. Motion is fluid but purposeful — scroll-driven reveals, weighted spring transitions. Asymmetric hero layouts force the eye to move. Nothing is decorative — every element earns its space.

- **Density:** 4/10 (Editorial Airy)
- **Variance:** 7/10 (Intentional Asymmetry)
- **Motion:** 6/10 (Fluid CSS, Spring Physics)

## 2. Color Palette & Roles
- **Deep Charcoal** (#111317) — Primary background, the stage everything plays on
- **Card Dark** (#161a20) — Elevated card surface, secondary sections
- **Card Darker** (#1c2028) — Tertiary depth layer, nested containers
- **Brand Gold** (#FFD24D) — THE single accent: CTAs, highlights, logo, active states, borders on hover. Never diluted.
- **Gold Dim** (#D4BC80) — Muted gold for secondary accent moments, italic serif text
- **Warm White** (#FFF9E6) — Primary text, headlines. Warm, never clinical
- **Steel Body** (#a0a8b4) — Body text, captions, metadata, secondary labels
- **Structural Border** (#2a2f3a) — Dividers, card edges, subtle separators

Banned: Pure black (#000000). Neon glows. Purple or blue accent variations. Cool grays mixed with warm grays.

## 3. Typography Rules
- **Display/Logo:** Jomhuria — signature brand mark font. Used exclusively for the logo wordmark. Bold, distinctive, Mediterranean character.
- **Headlines/Display:** Inter Black (900 weight) — Track-tight (-0.03em to -0.04em), controlled massive scale. Hierarchy through weight contrast.
- **Accent/Editorial:** Playfair Display Italic — Used sparingly for emotional emphasis moments, pull quotes, accent lines. Never in dashboards or UI chrome.
- **Body:** Inter (400–600 weight) — Relaxed leading (1.65–1.75), max 65ch per line, Steel Body color for secondary.
- **Scale:** clamp() for all display text. Min/max never forced to exact px.
- **Banned:** Generic system fonts. Centered body text. Underlines on non-links.

## 4. Component Stylings
- **Primary Button:** Brand Gold fill (#FFD24D), Deep Charcoal text (#111317), 6px radius, 800 weight, no outer glow. On hover: -2px translateY, gold box-shadow (rgba(255,210,77,0.35) spread). Tactile active state.
- **Ghost/Nav CTA:** Same gold fill at smaller size (9px 22px padding). Used in navbar.
- **Sticky Bar Button:** Smaller variant, flat.
- **Cards:** bg-card (#161a20) fill, 1px border (#2a2f3a), 12–14px border-radius. Border shifts to rgba(255,210,77,0.4) on hover. No drop shadows — elevation via background contrast only.
- **Stat Cards:** Large number (gold, 900 weight, massive clamp scale) over small Steel label. Centered. No icons.
- **Testimonial Cards:** Decorative large quote mark (96px, gold at 12% opacity) as background element. Text z-indexed above. Gradient from card to card2.
- **Badge/Pill:** Gold at 12% opacity background, gold border at 30% opacity, gold text, 999px radius. ★ prefix icon.
- **Editorial Lines:** Grid layout (110px label col + 1fr content). Gold left-border accent (4px) on punchy lines. Thin weight for contrast lines.
- **Modal:** bg-card fill, 16px radius, 40px padding, backdrop rgba(0,0,0,0.75).

## 5. Layout Principles
- Max-width 960px centered container, 24px side padding.
- Sections get 96px vertical padding (64px on mobile).
- Hero: photo bleeds right side (left: 32%, full height), text content max 640px on left. Left-to-right dark gradient overlay fades photo into background.
- Split sections: never equal columns — always deliberate proportion (left content, right visual).
- Stat rows: 3-column equal grid for data, collapses to 1-col on mobile.
- No absolute-positioned elements stacking over text. Clean spatial zones.
- Full-screen sections use min-height: 100vh with flex centering.

## 6. Motion & Interaction
- **Fade-up on scroll:** opacity 0→1, translateY 24px→0, 0.5s ease. Staggered siblings by 80ms index delay.
- **Hero entrance:** heroFadeUp keyframe, 0.6s ease, 0.1s delay.
- **CTA hover:** translateY(-2px) + gold box-shadow. 0.15s transition.
- **Countdown:** tabular-nums, 1s interval tick.
- **Sticky bar:** translateY(100%→0) on IntersectionObserver hero exit. 0.35s ease.
- **Scroll animations:** IntersectionObserver threshold 0.12, one-shot (unobserve after trigger).
- Hardware-accelerated: only transform and opacity animated. Never width/height/top/left.

## 7. Anti-Patterns (Banned)
- No emojis anywhere in the UI
- No neon outer glows or colored drop shadows
- No purple, blue, or teal accent colors
- No gradient text on headlines
- No equal 3-column card grids for features (only for data/stats)
- No centered hero layouts
- No "Scroll to explore" text, chevrons, or bouncing arrows
- No generic placeholder copy ("Lorem ipsum", "Learn More", "Get Started")
- No AI clichés: "Seamless", "Elevate", "Unleash", "Next-Gen", "Revolutionary"
- No custom mouse cursors
- No pure black backgrounds — always Deep Charcoal (#111317)
- No floating labels on inputs
- No circular loading spinners
- No decorative lines under section titles (use whitespace or background contrast instead)
- No warm/cool gray mixing — Zinc-based Steel palette only
