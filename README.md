## Image Compression Using Quadtree
### Overview

This project implements a quadtree-based image compression algorithm using Python. A quadtree is a tree data structure in which each internal node has exactly four children. It is particularly effective for spatial decomposition, making it useful for tasks like image compression, where the goal is to reduce the size of an image while preserving as much detail as possible.

### Quadtree Image Compression

The core idea behind quadtree image compression is to recursively divide an image into four quadrants (sub-images). This division continues until each quadrant reaches a predefined level of detail or a maximum depth is reached. The algorithm then approximates each quadrant with its average color, thereby compressing the image by reducing the amount of data needed to represent it.

### Steps Involved

1. **Initialization**:
   - The image is loaded and optionally resized based on a scale factor (`SIZE_MULT`).
   - The maximum depth (`MAX_DEPTH`) and detail threshold (`DETAIL_THRESHOLD`) are set to control the compression level.

2. **Quadrant Creation**:
   - The image is divided into quadrants recursively.
   - Each quadrant calculates its detail level based on color variance.
   - If the detail level of a quadrant is below the threshold or the maximum depth is reached, the division stops for that quadrant.

3. **Average Color Calculation**:
   - For each leaf quadrant (quadrants that are not further divided), the average color is calculated and used to fill the quadrant.

4. **Image Reconstruction**:
   - The compressed image is reconstructed by filling each quadrant with its average color.
   - An option to visualize the quadrant boundaries is available.

5. **Output Generation**:
   - The final compressed image is saved in JPEG format.
   - An animated GIF showing the progressive division of the image is also created.

### Features

- **Adjustable Parameters**:
  - `MAX_DEPTH`: Controls the maximum depth of the quadtree.
  - `DETAIL_THRESHOLD`: Determines the threshold for detail level, influencing how finely the image is divided.
  - `SIZE_MULT`: A multiplier to resize the image before processing.

- **Image and GIF Output**:
  - Generates a compressed image (`img_quadtree.jpg`).
  - Creates an animated GIF (`img_quadtree.gif`) to visualize the compression process.

- **Interactive User Input**:
  - Prompts the user for the image file name and desired depth of the quadtree.

### Example Use Case

Imagine you have a large, high-resolution image that you want to compress for web use. Using this quadtree algorithm, you can significantly reduce the image size while maintaining a visually acceptable level of detail. The resulting image is not only smaller in file size but also retains the essential visual features, making it ideal for web applications where load times and bandwidth are critical.

### Technical Details

- **Detail Calculation**:
  - The script uses a weighted average of the color histogram to calculate the detail level in each quadrant.
  - The detail intensity is a combination of red, green, and blue detail levels, weighted according to their perceptual importance.

- **Image Processing**:
  - The Pillow library is used for image loading, manipulation, and saving.
  - OpenCV and Matplotlib are utilized for additional image handling and plotting functionalities.

### Customization

Users can modify the following parameters in the script to customize the compression process:
- `MAX_DEPTH`: Adjust to change the depth of the quadtree.
- `DETAIL_THRESHOLD`: Set to control the detail level at which further division stops.
- `SIZE_MULT`: Change to resize the image before compression.
