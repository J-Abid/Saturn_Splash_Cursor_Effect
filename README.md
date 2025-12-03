# Saturn_Splash_Cursor_Effect #

Portfolio Asset with Saturn and splash cursor effect.

** Made by M. Junaid Abid **
-----

# Matte Gyro: High Voltage Edition ⚡🪐

**Matte Gyro** is an interactive, browser-based 3D visualization experiment that combines real-time fluid dynamics with WebGL rendering. It features a customizable gyroscopic planet, volumetric lighting, and a vertex-colored lightning simulation engine, all built with React and Three.js.

<img width="995" height="811" alt="Screenshot 2025-12-03 213846" src="https://github.com/user-attachments/assets/71385fb6-1f89-43a8-be4d-cd82d6030fa3" />

<img width="504" height="809" alt="Screenshot 2025-12-03 214052" src="https://github.com/user-attachments/assets/c64201ed-5fae-4392-9502-5c8fc9003a1e" />

## 🚀 Live Demo

https://j-abid.github.io/Saturn_Splash_Cursor_Effect/

-----

## ✨ Key Features

### 🌪️ Real-Time Fluid Simulation

  * **Custom WebGL Engine:** A fully custom fluid dynamics solver (advection, divergence, pressure, vorticity) running on the GPU.
  * **Interactive:** The fluid reacts to mouse movement with customizable splash force, radius, and dissipation.
  * **Visuals:** Supports high-resolution dye rendering with shading and bloom effects.

### ⚡ 3D Lightning Engine

  * **Procedural Generation:** Generates dynamic, "jagged" lightning geometry using Catmull-Rom curves and vector displacement.
  * **Vertex Coloring:** Implements gradient-based vertex coloring for smooth transitions between "Start" and "End" colors along the bolt.
  * **Volumetric Feel:** Uses additive blending and depth-test manipulation to create glowing, ethereal electricity effects.

### 🪐 Customizable Scene

  * **Interactive UI:** A "Cyberpunk" styled settings panel to control every aspect of the scene in real-time.
  * **Core Switching:** Toggle between a standard metallic planet, a Neutron Star core, or a Neptune-like gas giant.
  * **Environmental Effects:** Control star fields, asteroid belts, nebula clouds, and shooting stars.
  * **Gyroscope Rings:** Fully adjustable orbital rings with independent rotation speeds, roughness, and metalness controls.

-----

## 🛠️ Tech Stack

  * **Core:** [React 18](https://react.dev/)
  * **3D Rendering:** [Three.js](https://threejs.org/)
  * **Styling:** [Tailwind CSS](https://tailwindcss.com/)
  * **Transpiler:** [Babel](https://babeljs.io/) (Standalone for single-file portability)
  * **Icons:** FontAwesome

-----

## 🎮 How to Use

### Installation

No build process is required\! This project is designed as a **single-file application** for maximum portability.

1.  Clone the repository:
    ```bash
    git clone https://github.com/your-username/matte-gyro.git
    ```
2.  Open `index.html` in any modern web browser.

### Controls

  * **Rotate:** Click and drag the mouse to rotate the planetary system.
  * **Interact:** Move the mouse rapidly to trigger fluid splashes in the background.
  * **Settings:** Click the **Gear Icon** (bottom right) to open the configuration panel.
      * **CORE:** Adjust roughness, metalness, and rotation speed.
      * **RINGS:** Change ring colors, thickness, and animation patterns.
      * **COSMOS:** Toggle stars, lightning, and switch planet types (Neutron/Neptune).
      * **FLUID:** Customize the fluid simulation colors and physics.
  * **Edit Title:** Click directly on the main title ("MATTE GYRO") to rename the project live.

-----

## 🧠 Technical Highlights

### The Lightning Algorithm

The lightning effect is achieved by calculating a vector path between two points in 3D space. Instead of a straight line, the algorithm subdivides the path and applies perpendicular jitter (noise) to create the jagged look.

```javascript
// Simplified logic
const dir = new THREE.Vector3().subVectors(end, start);
const step = dir.normalize().multiplyScalar(length / segmentCount);

for(let i=1; i<segmentCount; i++) {
    curr.add(step);
    // Apply random 3D jitter
    const jitter = new THREE.Vector3(Math.random()-0.5, ...).multiplyScalar(1.5);
    points.push(curr.clone().add(jitter));
}
```

### Vertex Gradient Shader

To achieve the gradient look on the bolts without complex textures, the project calculates colors per-vertex based on the UV coordinates of the generated tube geometry.

```javascript
const t = uvs.getX(i); // Get position along tube (0 to 1)
const c = colorA.clone().lerp(colorB, t); // Interpolate color
colors[i * 3] = c.r; // Set vertex color
```

-----

## 📄 License

This project is licensed under the MIT License - see the GitHub MIT license for more details.

-----

**Created with ❤️ and Three.js**
