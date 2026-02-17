# Danso Infinite Product Slider 🎨

An immersive, infinite product carousel with smooth GSAP animations, dynamic product previews, and a unique circular navigation controller. This project showcases modern web animation techniques with a focus on fluid user interactions and visual appeal.

![Project Status](https://img.shields.io/badge/Status-In%20Development-yellow)
![GSAP](https://img.shields.io/badge/GSAP-3.12.2-green)
![ES6 Modules](https://img.shields.io/badge/ES6-Modules-blue)

---

## 🚧 Project Status

> **Note:** This project is currently **under active development**. The following components are incomplete or pending updates:
>
> - **script.js**: Additional functionality and event listeners will be implemented
> - **products.js**: Product data will be updated with unique names, prices, and URLs
> - **Assets**: Product images and other media assets are not yet added
> - **Known Bugs**: Some typos in the codebase (e.g., line 116 `ieym.element` should be `item.element`, line 144 `elemnt` should be `element`)

---

## ✨ Features

### Current Implementation

- **🎡 Infinite Carousel**: Seamless infinite scrolling with buffer-based rendering
- **🎯 Dynamic Scaling**: Active product scales to 1.25x, inactive to 0.75x
- **🎨 GSAP Animations**: Smooth transitions with custom easing functions
- **🖱️ Interactive Controller**: Unique circular navigation with animated close icon
- **📱 Product Preview**: Glassmorphism-based preview panel with product details
- **🖼️ Banner Transitions**: Dynamic background banner with scale animations
- **⚡ Performance Optimized**: Uses `will-change` CSS properties for GPU acceleration
- **📐 Responsive Layout**: Adapts to different screen sizes (mobile-first approach)

### Planned Features

- Complete event listener implementations
- Enhanced product interaction animations
- Additional navigation gestures (swipe, keyboard)
- Product filtering and categorization
- Shopping cart integration
- Accessibility improvements (ARIA labels, keyboard navigation)

---

## 🛠️ Technology Stack

| Technology | Version | Purpose |
|-----------|---------|---------|
| **GSAP** | 3.12.2 | Animation library for smooth transitions |
| **Ionicons** | 7.1.0 | Icon library for navigation elements |
| **ES6 Modules** | Native | Modular JavaScript architecture |
| **CSS Custom Properties** | - | Dynamic theming system |
| **DM Sans** | Variable | Primary font family |
| **DM Mono** | Regular | Monospace font for labels |

---

## 📁 Project Structure

```
Danso Infinite Product Slider/
│
├── fonts/
│   ├── DMMono-Regular.ttf              # Monospace font for labels
│   └── DMSans-VariableFont_opsz,wght.ttf  # Variable font for body text
│
├── products/                           # Product images (to be added)
│   ├── product-1.png
│   ├── product-2.png
│   └── ... (product-8.png)
│
├── index.html                          # Main HTML structure
├── style.css                           # Styles and animations
├── script.js                           # Core carousel logic
├── products.js                         # Product data array
└── README.md                           # This file
```

---

## 🎯 Core Concepts

### 1. Buffer-Based Infinite Scrolling

The carousel maintains a **buffer of 5 items** on each side of the active product:

```javascript
const BUFFER_SIZE = 5;
const spacing = 0.375; // 375px between items
const slideWidth = spacing * 1000;
```

**How it works:**
- Renders 11 items total: 5 before + 1 active + 5 after
- Removes items beyond the buffer and adds new ones dynamically
- Uses `relativeIndex` to track position relative to active item (0)

### 2. Relative Indexing System

Each slide has a `relativeIndex`:
- **0**: Active/centered product (scaled 1.25x)
- **-1, -2, ... -5**: Products to the left
- **+1, +2, ... +5**: Products to the right

When navigating:
- **Next**: All `relativeIndex` values decrease by 1
- **Prev**: All `relativeIndex` values increase by 1

### 3. Animation States

The carousel has multiple animation states managed by flags:

```javascript
let isPreviewAnimating = false;  // Preview panel is animating
let isPreviewOpen = false;       // Preview panel is open
```

**State Management:**
- Prevents navigation during animations
- Disables buttons when preview is open
- Ensures smooth state transitions

---

## 🎨 Design System

### Color Palette

```css
:root {
    --base-100: #fff;      /* White: backgrounds */
    --base-200: #999;      /* Gray: secondary text */
    --base-300: #343434;   /* Dark gray: inner controller */
    --base-400: #212121;   /* Darker gray: outer controller */
    --base-500: #000;      /* Black: primary elements */
}
```

### Typography

- **DM Sans (Variable)**: Body text, product names, buttons
- **DM Mono (Regular)**: Labels, tags, branding elements
- **Font sizes**: 0.75rem (tags) → 0.85rem (body) → 0.95rem (product names)

### Spacing & Layout

- **Container**: Full viewport height (`100vh`)
- **Products viewport**: 300×300px centered container
- **Product images**: 250×250px
- **Controller**: 11rem outer, 5rem inner circles
- **Preview panel**: 30% width, 75% height (mobile: calc(100% - 2rem))

---

## 🔧 Setup & Installation

### Prerequisites

- Modern web browser with ES6 module support
- Local development server (for module imports)

### Installation Steps

1. **Clone or download** the project:
   ```bash
   git clone <repository-url>
   cd "Danso Infinite Product Slider"
   ```

2. **Add product images** to the `/products/` directory:
   ```
   products/
   ├── product-1.png
   ├── product-2.png
   ├── ...
   └── product-8.png
   ```

3. **Start a local server**:
   ```bash
   # Using Python
   python -m http.server 8000

   # Using Node.js
   npx http-server

   # Using PHP
   php -S localhost:8000

   # Using VS Code Live Server extension
   Right-click index.html → "Open with Live Server"
   ```

4. **Open in browser**:
   ```
   http://localhost:8000
   ```

---

## 🎮 Usage

### Basic Navigation

- **Next Button**: Click the right arrow to move to the next product
- **Prev Button**: Click the left arrow to move to the previous product
- **Menu Controller**: Click the circular controller to open product preview (functionality pending)

### Adding Products

Edit `products.js` to add or modify products:

```javascript
const products = [
    {
        name: "Product Name",
        img: "/products/product-1.png",
        price: 249,
        tag: "category",
        url: "https://example.com/product"
    },
    // Add more products...
];
```

### Customization

**Adjust carousel spacing:**
```javascript
// In script.js
const spacing = 0.375; // Change this value (default: 375px)
```

**Modify animation duration:**
```javascript
// In script.js, updateSliderPosition()
duration: 0.75, // Change animation duration (seconds)
```

**Change color theme:**
```css
/* In style.css */
:root {
    --base-100: #your-color;
    /* Update other color variables */
}
```

---

## 📊 Code Architecture

### Main Components

#### 1. **Slide Management** (`addSlideItems`, `removeSlideItem`)
- Dynamically creates/removes DOM elements
- Sets initial GSAP transforms
- Maintains slide items array

#### 2. **Position Updates** (`updateSliderPosition`)
- Animates all slides to new positions
- Handles scaling based on active state
- Manages z-index layering

#### 3. **Navigation** (`moveNext`, `movePrev`)
- Updates current product index
- Manages buffer rotation
- Triggers content updates

#### 4. **Content Synchronization**
- `updateProductName()`: Top navigation display
- `updatePreviewContent()`: Preview panel data
- Banner image synchronization

#### 5. **Animation Controllers**
- `animateSlideItems()`: Hides/shows adjacent slides
- `animateSlideItemsControllerTransition()`: Controller morphing
- `updateButtonStates()`: Navigation button states

---

## 🐛 Known Issues & Fixes Needed

### Current Bugs

1. **Line 116 (script.js)**: Typo `ieym.element` → should be `item.element`
   ```javascript
   // Current (incorrect):
   ieym.element.dataset.relativeIndex = item.relativeIndex;
   
   // Should be:
   item.element.dataset.relativeIndex = item.relativeIndex;
   ```

2. **Line 144 (script.js)**: Typo `elemnt` → should be `element`
   ```javascript
   // Current (incorrect):
   gsap.to(item.elemnt, {
   
   // Should be:
   gsap.to(item.element, {
   ```

3. **Line 9-10 (index.html)**: Broken CDN URLs
   ```html
   <!-- Current (incorrect URLs): -->
   <script type="module" src="http:/unpfg.com/ionicon@7.1.0/..."></script>
   <script type="module" src="https://unkpg.com/ionicons@7.1.0/..."></script>
   
   <!-- Should be: -->
   <script type="module" src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.esm.js"></script>
   <script nomodule src="https://unpkg.com/ionicons@7.1.0/dist/ionicons/ionicons.js"></script>
   ```

4. **Line 223 (style.css)**: Typo `rdgb` → should be `rgba`
   ```css
   /* Current (incorrect): */
   background-color: rdgb(255, 255, 255, 0.3);
   
   /* Should be: */
   background-color: rgba(255, 255, 255, 0.3);
   ```

### Incomplete Functionality

- [ ] Controller click event listener
- [ ] Preview panel open/close animations
- [ ] Keyboard navigation (arrow keys)
- [ ] Touch/swipe gestures for mobile
- [ ] "View Details" button functionality
- [ ] Product data completion (unique names, prices, URLs)

---

## 🎯 Performance Optimizations

### Current Optimizations

1. **GPU Acceleration**:
   ```css
   will-change: transform;  /* Slides */
   will-change: clip-path;  /* Controller */
   will-change: opacity;    /* Various elements */
   ```

2. **Efficient DOM Management**:
   - Only renders visible items + buffer
   - Removes off-screen elements
   - Reuses slide instances

3. **GSAP Best Practices**:
   - Uses `power3.out` easing for natural motion
   - Batches animations for frame consistency
   - Leverages GSAP's RAF (RequestAnimationFrame)

### Potential Improvements

- [ ] Implement lazy loading for product images
- [ ] Add image preloading for smoother transitions
- [ ] Use `IntersectionObserver` for visibility detection
- [ ] Implement virtual scrolling for 100+ products
- [ ] Add debouncing to rapid navigation clicks

---

## 🎨 Animation Details

### Transition Timings

| Element | Duration | Easing | Notes |
|---------|----------|--------|-------|
| Slide position | 0.75s | `power3.out` | Smooth deceleration |
| Controller clip-path | 0.75s | `power3.inOut` | Symmetrical easing |
| Close icon reveal | 0.4s | `power3.out` | Staggered by 0.1s |
| Nav button fade | 0.2s | `power3.out` | Quick transition |

### GSAP Configuration

```javascript
// Slide animation example
gsap.to(item.element, {
    x: relativeIndex * slideWidth,     // Horizontal position
    scale: isActive ? 1.25 : 0.75,     // Size based on state
    zIndex: isActive ? 100 : 1,        // Layer management
    duration: 0.75,                    // Animation duration
    ease: "power3.out"                 // Easing function
});
```

---

## 🌐 Browser Compatibility

### Tested Browsers

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

### Required Features

- CSS Custom Properties (CSS Variables)
- CSS `clip-path`
- CSS `backdrop-filter`
- ES6 Modules (`import`/`export`)
- `will-change` property
- GSAP 3.x support

### Fallbacks Needed

- `backdrop-filter` (for older browsers)
- ES6 module syntax (transpile with Babel if needed)

---

## 📱 Responsive Design

### Breakpoints

```css
@media (max-width: 1000px) {
    .product-preview {
        width: calc(100% - 2rem);  /* Full width on mobile */
    }
}
```

### Mobile Considerations

- Preview panel expands to near-full width
- Touch-friendly button sizes
- Optimized image sizes
- Reduced animation complexity (future enhancement)

---

## 🚀 Future Enhancements

### Phase 1: Core Completion
- [ ] Fix all known bugs/typos
- [ ] Add unique product data
- [ ] Implement controller interactions
- [ ] Complete preview panel animations

### Phase 2: User Experience
- [ ] Add keyboard navigation
- [ ] Implement touch/swipe gestures
- [ ] Add accessibility features (ARIA, focus management)
- [ ] Create loading states

### Phase 3: Advanced Features
- [ ] Product filtering/search
- [ ] Multiple categories
- [ ] Shopping cart integration
- [ ] Product favorites/wishlist
- [ ] Share functionality

### Phase 4: Polish
- [ ] Add sound effects
- [ ] Implement micro-interactions
- [ ] Create tutorial/onboarding
- [ ] Add analytics tracking

---

## 🤝 Contributing

This project is currently under development. Contributions are welcome once the core functionality is complete.

### Development Workflow

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Fix bugs from the "Known Issues" section
4. Test thoroughly across browsers
5. Commit your changes: `git commit -m 'Add amazing feature'`
6. Push to the branch: `git push origin feature/amazing-feature`
7. Open a Pull Request


