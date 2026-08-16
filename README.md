# 🎮 Pokédex Web Application

A modern, responsive Pokédex web application that uses the [PokéAPI](https://pokeapi.co/) to display detailed information about Pokémon.

![Pokédex Banner](https://img.shields.io/badge/Pok%C3%A9món-API-ffcc00?style=for-the-badge&logo=pokemon)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-Responsive-1572B6?style=for-the-badge&logo=css3)

## 🌐 Live Demo

👉 **[pokedex.viktor-wilhelm.de](https://pokedex.viktor-wilhelm.de/)**

> 💡 **Tip:** Ctrl + Click → open Live Demo in a new tab

## 🚀 Features

### Core Features

- ✨ **Modern UI** with glassmorphism effects
- 🔍 **Live Search** with autocomplete
- 📱 **Fully Responsive** (320px - 1920px+)
- ⚡ **Performance Optimized** with caching
- ♿ **Accessibility** (ARIA labels, keyboard navigation)
- 🎨 **Type-based Color Scheme**
- 🌙 **Smooth Animations & Transitions**

### Additional Features

- 🎯 **Smart Search**:
  - 3-character minimum validation
  - Autocomplete with top 8 suggestions
  - Search by name or ID
- 💾 **Smart Caching**: Previously loaded Pokémon are cached
- 🔄 **Error Handling**: Global error handlers with user feedback
- 📊 **Detailed Stats**: Visualized bars for all values
- 🎮 **Keyboard Navigation**: Arrow keys in modal
- 🔔 **Notification Feedback**: User feedback when a search yields no results

## 🛠️ Technology Stack

```
Frontend:
├── Vanilla JavaScript (ES6+)
├── CSS3 (Grid, Flexbox, Custom Properties)
├── HTML5 Semantic Markup
└── Module-based Architecture

API:
└── PokéAPI v2 (REST)

Tools:
├── Git & GitHub
└── VS Code
```

## 📁 Project Structure

```
Pokedex/
├── assets/
│   ├── icons/           # SVG Icons (Pokéball, Search, etc.)
│   └── images/          # Screenshots used in this README
├── scripts/
│   ├── main.js         # App Entry Point
│   ├── api.js          # PokéAPI Integration
│   ├── pokemon-detail.js # Modal Logic
│   ├── pokemon-list.js # Card Rendering
│   ├── search.js       # Search & Autocomplete
│   ├── ui-helpers.js   # UI Utility Functions
│   ├── constants.js    # Configuration & Constants
│   ├── footer.js       # Footer Logic
│   ├── components/
│   │   └── notification.js
│   └── templates/
│       ├── footer-templates.js
│       ├── modal-template.js
│       ├── notification-template.js
│       ├── pokemon-card-template.js
│       ├── pokemon-details-template.js
│       └── ui-elements-template.js
├── styles/
│   ├── global.css      # Global Styles & Variables
│   ├── layout.css      # Layout System
│   ├── components/     # Component-Specific Styles
│   │   ├── buttons.css
│   │   ├── footer.css
│   │   ├── header.css
│   │   ├── legal-modal.css
│   │   ├── loading.css
│   │   ├── modal.css
│   │   ├── notification.css
│   │   ├── pokemon-card.css
│   │   ├── pokemon-detail.css
│   │   └── search.css
│   └── utilities/      # Utility Styles
│       ├── animations.css
│       ├── responsive-accessibility.css
│       ├── responsive-desktop.css
│       ├── responsive-mobile.css
│       └── responsive-tablet.css
├── index.html          # Main HTML File
├── .gitignore
└── README.md
```

## 🎯 Code Architecture

### Modular JavaScript Structure

```javascript
// Example from api.js:

let processPokemonListResponse = async (data, offset) => {
  appState.currentOffset = offset;
  const pokemonDetails = await fetchPokemonDetails(data.results);
  appState.pokemonList.push(...pokemonDetails);
  return pokemonDetails;
};

export let fetchPokemonList = async (offset, limit) => {
  const url = `${API_CONFIG.baseUrl}${API_CONFIG.endpoints.pokemon}?offset=${offset}&limit=${limit}`;

  const response = await fetch(url);
  if (!response.ok) {
    throw new Error(`API Error: ${response.status}`);
  }

  const data = await response.json();
  return await processPokemonListResponse(data, offset);
};
```

### Template System

All HTML templates are outsourced to separate functions:

```javascript
// templates/
export function createPokemonCardHTML(pokemon) { ... }
export function createModalHTML(pokemon) { ... }
export function createStatsHTML(stats) { ... }
```

## 📱 Responsive Breakpoints

Simplified overview of the main responsive ranges (Mobile-First Approach):

```css
/* Base: 320px - 479px */

@media (min-width: 480px) {
  /* Small Tablets */
}
@media (min-width: 768px) {
  /* Tablets */
}
@media (min-width: 1024px) {
  /* Desktop */
}
@media (min-width: 1440px) {
  /* Large Desktop */
}
```

Additional fine-grained breakpoints and accessibility-related media queries (e.g. `prefers-reduced-motion`, `prefers-contrast`) exist in `styles/utilities/responsive-*.css`.

## 🎨 Design Principles

- **Mobile-First**: Optimized for small screens first
- **Accessibility**: ARIA labels on key interactive elements, keyboard navigation
- **Performance**: Lazy loading, caching, optimized images
- **UX**: Clear feedback mechanisms, intuitive navigation
- **Clean Code**: Max 14 lines per function, clear naming conventions

## 🚦 Installation & Setup

```bash
# Clone the repository
git clone https://github.com/viktor-wilhelm/Pokedex.git

# Navigate to the directory
cd Pokedex

# Start a local server (e.g., Live Server in VS Code)
# Or use Python's built-in HTTP server:
python3 -m http.server 8000

# Open in your browser
# http://localhost:8000
```

## 🔍 Usage

1. **Browse Pokémon**: Scroll through the list or use the search function
2. **Search**: Enter at least 3 characters for autocomplete suggestions
3. **View Details**: Click on a Pokémon card to open the modal
4. **Modal Navigation**: Use arrow keys or arrow buttons (← →)
5. **Load More**: Click "Load More Pokémon" to fetch additional Pokémon

## 📊 Performance Optimizations

- ✅ **API Caching**: Prevents redundant network requests
- ✅ **Lazy Loading**: Details are only loaded when needed
- ✅ **Image Optimization**: High-quality images from official sources

## 🐛 Known Limitations

- PokéAPI availability and usage are subject to the API provider's fair-use policy.
- No offline functionality (PWA could be implemented)

## 🔮 Future Enhancements

- [ ] Favorites system with LocalStorage
- [ ] Filter function by type, generation
- [ ] Pokémon comparison feature
- [ ] Dark Mode toggle
- [ ] Progressive Web App (PWA)
- [ ] Multi-language support

## 👨‍💻 Developer

**Viktor Wilhelm**

- 📧 Email: [hello@viktor-wilhelm.de](mailto:hello@viktor-wilhelm.de)
- 💼 LinkedIn: [Viktor Wilhelm](https://www.linkedin.com/in/viktor-wilhelm)
- 💻 GitHub: [viktor-wilhelm](https://github.com/viktor-wilhelm)

## 📝 License

This project was created for learning purposes. Pokémon and all related characters are the property of Nintendo, Game Freak, and Creatures Inc.

## 🙏 Acknowledgments

- **PokéAPI**: For providing a comprehensive and free API
- **Nintendo/Game Freak**: For the Pokémon franchise
- All developers contributing to the open-source community

---

## 📸 Screenshots

![Pokédex Screenshot](./assets/images/pokedex_screenshot,.png)

---

**⭐ If you like this project, please give it a star on GitHub!**
