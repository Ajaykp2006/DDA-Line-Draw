# DDA Line Algorithm Visualizer

An interactive, web-based tool designed to visualize the **Digital Differential Analyzer (DDA)** line-drawing algorithm on a pixelated grid canvas. This visualizer provides a real-time, interactive environment to observe how lines are rasterized onto discrete grid cells from given coordinates.

## 🔗 Important Links
- **Live Website:**[DDA-Line-Draw Visualizer:](https://script.google.com/macros/s/AKfycbwWko-5qWWstLSFF_LCLdVhSZVrWvYZgky9JWec7vRcXzVerBhZITv8vTtiLemd9buw/exec)

## 📸 Screenshot
![DDA-Line-Draw Visualizer PageScreenshot] <img width="1917" height="1090" alt="Screenshot 2026-07-18 033049" src="https://github.com/user-attachments/assets/1290e78d-887c-4004-848d-712a18096d96" />

## Features

- **Interactive Canvas Grid:** A 20×20 pixelated grid that translates float coordinates into concrete pixel rasterizations.
- **Custom Coordinate Controls:** Input fields for start points $(X_1, Y_1)$ and end points $(X_2, Y_2)$ bounded between a 0 to 19 axis matrix.
- **Visual Color Markers:**
  - **Blue Pixel:** Exact start coordinate entry point.
  - **Red Pixel:** Exact end coordinate entry point.
  - **Green Pixels:** Generated incremental rasterized path elements.
- **Dynamic Calculation Rendering:** Instantaneous step calculations upon clicking **Calculate & Draw**.
- **Responsive Layout:** Adaptive layout cards with standard semantic validation rules.

---

## Technical Details & Core Algorithm

The Digital Differential Analyzer (DDA) is an incremental scan-conversion line algorithm. It characterizes lines by evaluating the differences along the coordinate axes ($\Delta x$ and $\Delta y$) and using interpolation to map continuous paths onto discrete pixel locations.

### Algorithm Summary
1. Calculate the difference over the coordinate planes:
   $$\Delta x = X_2 - X_1$$
   $$\Delta y = Y_2 - Y_1$$
2. Determine the number of steps required by evaluating the maximum absolute difference:
   $$	ext{Steps} = \max(|\Delta x|, |\Delta y|)$$
3. Compute the incremental adjustments needed for each raster loop phase:
   $$X_{	ext{inc}} = rac{\Delta x}{	ext{Steps}}$$
   $$Y_{	ext{inc}} = rac{\Delta y}{	ext{Steps}}$$
4. Iteratively loop through the structural step values, accumulating increments and mapping coordinates to grid addresses using nearest-neighbor rounding functions:
   $$X_{k+1} = X_k + X_{	ext{inc}}$$
   $$Y_{k+1} = Y_k + Y_{	ext{inc}}$$
   $$	ext{Pixel}(X, Y) = \left( \lfloor X + 0.5 
floor, \lfloor Y + 0.5 
floor 
ight)$$

---

## File Structure & Usage

The implementation is entirely self-contained within a single HTML document (`index.html` or equivalent file name). It utilizes inline CSS styles for structure and native vanilla JavaScript for modern Canvas API updates.

### Running the Visualizer Locally
1. Copy the code into a standard file named `index.html`.
2. Open the file in any modern web browser (Chrome, Firefox, Safari, Edge, etc.) by double-clicking it or dragging it into a browser tab.
3. Alter the start or end coordinate values in the configuration sidebar.
4. Click **Calculate & Draw** to generate the pixel path, or **Clear Grid** to wipe the canvas environment state.

---

## Visualizer Stylesheet Specs
- **Background Palette:** `#f0fdf4` (Soft Mint)
- **Primary Color Accents:** `#16a34a` (Emerald), `#2563eb` (Royal Blue), `#ef4444` (Coral Red)
- **Typography:** Segoe UI system fonts
- **Canvas Matrix Resolution:** 400px by 400px mapped into uniform 20px cell dimensions.
