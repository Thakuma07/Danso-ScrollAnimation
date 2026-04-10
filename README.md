# Danso Infinite Product Slider 🎨

An immersive, high-performance infinite product carousel built with **GSAP**, featuring smooth animations, glassmorphism-inspired previews, and a unique circular navigation controller.

![License](https://img.shields.io/badge/license-ISC-blue)
![GSAP](https://img.shields.io/badge/GSAP-3.12.2-green)
![Vite](https://img.shields.io/badge/Vite-8.0.8-646CFF)
![Responsive](https://img.shields.io/badge/Responsive-Yes-brightgreen)

---

## ✨ Features

- 🎡 **Infinite Carousel**: Seamless infinite scrolling using a buffer-based rendering system.
- 🎯 **Dynamic Scaling**: Active products dynamically scale (1.25x) while inactive items shrink (0.75x) for focus.
- 🎨 **GSAP Powered**: Ultra-smooth transitions and micro-animations for a premium feel.
- 🔍 **Product Preview**: Detailed preview panel with glassmorphism effects and dynamic banner transitions.
- 🖱️ **Interactive Controller**: Custom-built circular navigation with animated state transitions.
- ⚡ **Optimized Performance**: Hardware-accelerated animations using `will-change` and efficient DOM recycling.
- 📱 **Mobile Responsive**: Fully adaptive layout that scales beautifully across all devices.

---

## 🛠️ Tech Stack

- **Core**: HTML5, CSS3 (Vanilla), JavaScript (ES6+)
- **Animation**: [GSAP](https://greensock.com/gsap/) (GreenSock Animation Platform)
- **Icons**: [Ionicons](https://ionicons.com/)
- **Bundler**: [Vite](https://vitejs.dev/)
- **Typography**: DM Sans (Variable) & DM Mono

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (latest LTS recommended)
- [npm](https://www.npmjs.com/)

### Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Thakuma07/DansoInfinite-ScrollAnimation.git
   cd "Danso Infinite Product Slider"
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Product Images**:
   Add your product images to `public/products/`. The files should follow the naming convention `product-1.png`, `product-2.png`, etc., as defined in `products.js`.

4. **Run development server**:
   ```bash
   npm run dev
   ```

5. **Build for production**:
   ```bash
   npm run build
   ```

---

## 📁 Project Structure

```text
Danso-Infinite-Slider/
├── public/                 # Static assets
│   ├── fonts/              # Project typography
│   └── products/           # Product images (add here)
├── index.html              # Entry point
├── style.css               # Core design & animations
├── script.js               # Carousel logic & GSAP timelines
├── products.js             # Product data configuration
├── package.json            # Project dependencies & scripts
└── README.md               # You're here!
```

---

## ⚙️ Customization

### Adding Products
Edit `products.js` to update names, prices, and tags. The carousel will automatically adapt to the number of items.

```javascript
{
    name: "New Product",
    img: "/products/new-item.png",
    price: 199,
    tag: "Category",
    url: "#"
}
```

### Animation Tuning
Modify constants in `script.js` to change the feel of the carousel:

- `spacing`: Adjust the distance between items.
- `duration`: Change animation speed (default `0.75s`).
- `BUFFER_SIZE`: Control how many items are rendered off-screen.

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve the slider, feel free to fork the repo and submit a PR. 

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📜 Credits & Attribution

- Design inspired by the **Danso** landing page concept.
- Developed by [Thakuma07](https://github.com/Thakuma07).
- Icons provided by [Ionicons](https://ionicons.com/).

---

Developed with ❤️ by Arkyadeep Pal
