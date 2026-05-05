# SKILL::TREE // Cyberpunk

A cyberpunk-themed skill tree web app with 3D avatars. Track your skills, check off sub-skills, and watch your character emote as you level up.

Built with React, Three.js, and Zustand.

---

## Features

- 3D avatar display with auto-scaling and animation support
- Expandable skill sidebar with sub-skill completion tracking
- Real-time skill badge showing active skill progress
- Editable player name
- Swappable avatars (`.glb` models) and backgrounds
- Custom image upload for backgrounds
- All data persisted in localStorage
- Cyberpunk UI with neon glow, glitch text, and scanlines

---

## Prerequisites

- [Node.js](https://nodejs.org/) v18 or higher
- npm (comes with Node.js)

---

## Getting Started

### 1. Clone the repository

```bash
git clone https://gitlab.com/<your-username>/skill-tree.git
cd skill-tree
```

### 2. Install dependencies

```bash
npm install
```

### 3. Start the dev server

```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

### 4. Build for production

```bash
npm run build
npm run preview   # preview the production build locally
```

The production output is in the `dist/` folder.

---

## Usage

| Action | How |
|--------|-----|
| **View skills** | Skills are listed in the left sidebar |
| **Expand a skill** | Click any skill row to see its sub-skills |
| **Complete a sub-skill** | Click a sub-skill row — the avatar emotes and a level-up flash plays |
| **Add a skill** | Click the `+` button in the sidebar header |
| **Edit a skill** | Hover a skill and click the pencil icon |
| **Delete a skill** | Open the skill editor and click Delete |
| **Change player name** | Click the name button (top right), type a new name, press Enter |
| **Change avatar** | Click Avatar (bottom right), pick a model |
| **Change background** | Click Background (bottom right), pick a gradient/color/image or upload one |
| **Resize sidebar** | Drag the right edge of the sidebar |

All changes (skills, name, avatar, background) are saved to your browser and persist across page reloads.

---

## Adding Your Own Content

### Add a new 3D avatar

1. Place your `.glb` file in `public/models/`
2. Add an entry in `src/data/avatars.js`:
   ```js
   { name: 'My Character', path: '/models/My_Character.glb' },
   ```
3. The model is auto-scaled to fit the viewport.

For emote support, bake an `Idle` and `Emote` animation action into the `.glb` file using Blender.

### Add a new background image

1. Place the image in `public/backgrounds/`
2. Add an entry in `src/data/backgrounds.js` under `images`:
   ```js
   { name: 'Night City', file: 'night_city.jpg' },
   ```

---

## Project Structure

```
skill-tree/
├── public/
│   ├── models/          # .glb avatar models
│   └── backgrounds/     # Background images
├── src/
│   ├── main.jsx         # Entry point
│   ├── App.jsx          # Root layout + loader
│   ├── App.css          # All styles
│   ├── store/
│   │   └── useSkillStore.js   # Zustand state (persisted)
│   ├── data/
│   │   ├── defaultSkills.js   # Default skills & neon colors
│   │   ├── avatars.js         # Avatar list
│   │   └── backgrounds.js     # Background presets
│   ├── components/
│   │   ├── canvas/
│   │   │   ├── Scene.jsx      # Three.js scene setup
│   │   │   └── Character.jsx  # 3D model loading & animation
│   │   ├── ui/
│   │   │   ├── SkillSidebar.jsx     # Resizable sidebar
│   │   │   ├── SkillList.jsx        # Skill accordion
│   │   │   ├── SkillBadge.jsx       # Active skill badge
│   │   │   ├── NameBadge.jsx        # Player name editor
│   │   │   ├── AvatarPicker.jsx     # Avatar selector
│   │   │   ├── BackgroundPicker.jsx # Background selector
│   │   │   └── SkillEditor.jsx      # Skill create/edit modal
│   │   └── effects/
│   │       └── GlitchText.jsx       # Glitch text animation
├── index.html
├── vite.config.js
└── package.json
```

---

## Tech Stack

| Technology | Purpose |
|------------|---------|
| [React](https://react.dev/) 19 | UI framework |
| [Three.js](https://threejs.org/) | 3D rendering |
| [@react-three/fiber](https://docs.pmnd.rs/react-three-fiber) | React renderer for Three.js |
| [@react-three/drei](https://github.com/pmndrs/drei) | Three.js helpers (glTF loader, controls, environment) |
| [Zustand](https://github.com/pmndrs/zustand) | State management with localStorage persistence |
| [Vite](https://vite.dev/) | Build tool and dev server |

---

## Contributing

### Setting up for development

1. Fork the repository on GitLab
2. Clone your fork:
   ```bash
   git clone https://gitlab.com/<your-username>/skill-tree.git
   cd skill-tree
   ```
3. Create a feature branch:
   ```bash
   git checkout -b feature/your-feature-name
   ```
4. Install dependencies and start dev server:
   ```bash
   npm install
   npm run dev
   ```

### Making changes

- **UI components** are in `src/components/ui/`
- **3D components** are in `src/components/canvas/`
- **State logic** is in `src/store/useSkillStore.js`
- **All styles** are in `src/App.css` (single file, organized by section)
- **Static data** (avatars, backgrounds, default skills) is in `src/data/`

### Submitting your changes

1. Verify the build passes:
   ```bash
   npm run build
   ```
2. Commit your changes with a clear message:
   ```bash
   git add <files>
   git commit -m "Add: description of what you added"
   ```
3. Push to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
4. Open a Merge Request on GitLab targeting the `main` branch.

### Contribution ideas

- New background gradients or preset colors
- Additional 3D avatar models (`.glb` with Idle/Emote animations)
- Skill import/export (JSON)
- Sound effects on level up
- Skill dependency trees (prerequisite sub-skills)
- Mobile responsive layout
- Shareable skill cards (screenshot/image export)

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| Blank page on load | Open browser console, clear localStorage: `localStorage.clear()`, then reload |
| Avatar too small/large | Models auto-scale. If it still looks off, the `.glb` may have unusual geometry — check its bounding box in Blender |
| Background image not showing | Ensure the filename in `backgrounds.js` matches the file in `public/backgrounds/` exactly |
| "Failed to load avatar model" | The `.glb` file may be missing or corrupt. Select a different avatar |

---

## License

This project uses 3D models from [Sketchfab](https://sketchfab.com/) under Creative Commons licenses. Credits to the original creators.
