# TapToMoon Design Guidelines

## Design Approach: Reference-Based Gaming

**Primary References:** Hamster Kombat, NOTCOIN, Blum, Catizen tap-to-earn games
**Aesthetic:** Dark gaming interface with high-energy visuals, celebratory animations, and crypto/web3 premium feel

## Typography System

**Font Family:** 
- Primary: 'Inter' or 'DM Sans' (Google Fonts) - clean, modern readability
- Accent: 'Orbitron' or 'Rajdhani' (Google Fonts) - tech/gaming feel for headers and numbers

**Hierarchy:**
- Mega numbers (points/scores): text-5xl to text-7xl, font-bold
- Page titles: text-3xl to text-4xl, font-bold
- Section headers: text-xl to text-2xl, font-semibold
- Card titles: text-lg, font-semibold
- Body text: text-base, font-medium
- Micro text (timers, stats): text-sm, font-medium
- Button text: text-base to text-lg, font-semibold

## Layout System

**Spacing Primitives:** Tailwind units of 2, 4, 6, 8, 12, 16
- Micro spacing (badges, icons): p-2, gap-2
- Component padding: p-4, p-6
- Section spacing: py-8, py-12
- Screen padding: px-4, px-6

**Screen Structure:**
- Fixed bottom navigation bar (h-16)
- Scrollable content area with pb-20 to clear nav
- Full-width cards and sections
- max-w-lg centered container for content

## Core Components

### Main Tap Screen (Home)
- Top stats bar: Energy counter (current/max), points display with animated counting
- Center stage: Large animated coin/tap target (min-h-[400px])
- Tap target: Circular, centered, 60-70% viewport width
- Energy bar: Full-width progress bar below header, gradient fill
- Bottom info: Current multiplier, active boosts with countdown timers

### Cards & Containers
- Rounded corners: rounded-xl for major cards, rounded-lg for nested items
- Padding: p-6 for cards, p-4 for list items
- Borders: Subtle glowing borders for premium/active items
- Elevation: Use subtle shadows (shadow-lg) for floating elements

### Boost Shop Grid
- 2-column grid on mobile (grid-cols-2 gap-4)
- Each boost card: Vertical layout with icon top, title, price, purchase button
- Premium boosts: Highlighted with glow treatment
- Disabled state: opacity-50 with lock icon

### Navigation
- Bottom fixed nav: 5 tabs (Home, Boosts, Friends, NFTs, Profile)
- Icon + label for each tab
- Active state: Glow effect and scale transform
- Icon size: w-6 h-6 minimum for tap targets

### Buttons
- Primary CTA: Large, full-width or prominent (h-12 to h-14)
- Purchase buttons: Glow effect, price prominently displayed
- Disabled state: opacity-50, cursor-not-allowed
- Touch targets: Minimum h-12 for mobile taps

### Stats & Counters
- Large animated numbers with gradient text treatment
- Progress bars: Full-width, rounded-full, gradient fills
- Timers: Monospace numbers, countdown format (HH:MM:SS)
- Stat cards: Icon + number + label in compact horizontal layout

### Lists (Friends, NFTs)
- Avatar/icon on left (w-12 h-12, rounded-full)
- Info column: Name/title + subtitle/stats
- Right action: Points/rank/rarity badge
- Dividers: Subtle separators between items
- Infinite scroll or pagination for long lists

### Modals & Overlays
- Full-screen overlay with backdrop blur
- Content card: max-w-md, centered vertically and horizontally
- Close button: Top-right, prominent
- Confirmation buttons: Full-width at bottom

### NFT Drop Interface
- Center card flip/reveal animation container
- Rarity indicators: Color-coded badges/borders
- Drop button: Large, centered, countdown timer above
- Collection display: Grid of collected NFTs (grid-cols-3 gap-2)

### Daily Combo
- 3 card slots in horizontal row
- Cards: Flip animation, tap to reveal
- Submit button: Appears when 3 selected
- Reward display: Celebratory animation on success

## Animations & Effects

**Minimal but Impactful:**
- Tap feedback: Scale pulse on coin tap (scale-95 to scale-105)
- Success celebrations: Confetti particle effect (library: canvas-confetti)
- Number counting: Animated increment for point displays
- Purchase success: Glow pulse + scale animation
- Card flips: CSS 3D transforms for NFT/combo reveals
- Loading states: Spinning gradient border (animate-spin)

**No Animations For:**
- Page transitions (instant)
- Scroll effects
- Background movements
- Excessive micro-interactions

## Icons

**Library:** Heroicons (via CDN)
- Coin/currency icons
- Energy/lightning icons
- Gift/present for rewards
- Users for friends system
- Sparkles for NFTs/premium
- Lock for unavailable items
- Chart/stats icons

## Accessibility

- All interactive elements: min-h-12, min-w-12
- Clear focus states with outline rings
- Sufficient contrast for all text
- Loading states for async actions
- Error states with clear messaging
- Touch targets with adequate spacing (gap-4 minimum)

## Images

**Hero/Main Tap Area:**
- Animated coin/logo: SVG or Lottie animation, centered, large (300-400px)
- Background: Gradient treatment with subtle pattern/texture overlay (no actual image needed - CSS gradients)

**NFT Cards:**
- Placeholder images for NFT tiers using gradient placeholders until real assets load
- Rarity backgrounds: Different gradient treatments per tier

**Profile/Avatar:**
- Telegram user avatars via initData when available
- Fallback: Gradient circle with user initials

No large hero images required - this is a full-screen interactive gaming app where the tap target IS the hero element.