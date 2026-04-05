![Vue 3 Parametric 3D Viewer](src/assets/3d-viewer-demo.gif)

# Parametric 3D Viewer | Vue 3 |  [Live Demo]()
A quick prototype to demonstrate Vue 3 reactivity integrated with a Three.js rendering engine.

![Vue 3](https://img.shields.io/badge/Vue.js-000000?style=for-the-badge&logo=vue.dot.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white)
![GSAP](https://img.shields.io/badge/GSAP-88CE02?style=for-the-badge&logo=greensock&logoColor=white)
![Sass (SCSS)](https://img.shields.io/badge/Sass(SCSS)-hotpink?style=for-the-badge&logo=sass&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)

## Architecture

```bash
├── src/
│   ├── assets/             
│   ├── components/
│   │   ├── Viewer3D.vue    # Canvas
│   │   └── Controls.vue    # UI panel (Inputs)
│   ├── core/
│   │   └── SceneManager.ts # Three.js (Logic)
│   ├── App.vue             
│   └── main.ts             
├── index.html
└── package.json
```

## Tech Stack

- **Vue 3**
- **Three.js**
- **GSAP**
- **Vite**
- **Sass**

## Installation
```Bash
# Clone the repository
git clone https://github.com/kolonatalie/vue3-parametric-3D-viewer

# Install dependencies
npm install

# Start development server
npm run dev
```

## Available Scripts

|  |  |
| :--- | :--- |
|`npm run dev`| Starts Vite dev server at `http://localhost:3000` |
|`npm run build`| Builds the project.|
|`npm run preview`| Locally previews the production build|
|`npm run lint`| Audits JS/TS and SCSS for errors.|
|`npm run lint:fix` | Automatically fixes linting and styling issues.|

---

## Connect with Me

I'm always open to discussing creative technology, motion design, or potential collaborations.

[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-563D6F?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/kolonatalie/)
[![X Badge](https://img.shields.io/badge/X-8A62B3?style=for-the-badge&logo=x&logoColor=white)](https://x.com/dev_kolonatalie)
[![Bluesky Badge](https://img.shields.io/badge/Bluesky-A575D4?style=for-the-badge&logo=bluesky&logoColor=white)](https://bsky.app/profile/kolonatalie.bsky.social)
[![Mastodon Badge](https://img.shields.io/badge/Mastodon-704F91?style=for-the-badge&logo=mastodon&logoColor=white)](https://mastodon.social/@kolonatalie)
[![GitHub Badge](https://img.shields.io/badge/GitHub-3D2B4F?style=for-the-badge&logo=github&logoColor=white)](https://github.com/kolonatalie)