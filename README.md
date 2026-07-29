# PixView

A lightweight image viewer written in C that renders binary PPM (P6) images using SDL2.

PixView is a minimal graphics application built to explore image parsing, raster rendering, and event-driven programming in C. It reads binary PPM (P6) images from standard input, decodes their pixel data, and displays them in an SDL2 window.

The project demonstrates the fundamentals of graphics programming while maintaining a compact and easily understandable codebase.

---

## Features

- Binary PPM (P6) image support
- SDL2-based rendering
- Standard input image streaming
- Lightweight implementation in C
- Event-driven window management
- Portable and easy to build

---

## Preview

*Screenshot or GIF goes here.*

---

## Tech Stack

| Component | Technology |
|----------|------------|
| Language | C |
| Graphics Library | SDL2 |
| Image Format | Binary PPM (P6) |

---

## Requirements

- GCC or Clang
- SDL2 development libraries

Ubuntu/Debian

```bash
sudo apt install libsdl2-dev
```

macOS

```bash
brew install sdl2
```

---

## Building

```bash
gcc image_viewer.c -o pixview -lSDL2
```

---

## Usage

Run the viewer by piping a binary PPM image into standard input.

```bash
./pixview < image.ppm
```

Or generate a PPM image dynamically using ImageMagick.

```bash
convert input.jpg ppm:- | ./pixview
```

---

## Implementation

PixView performs the following steps:

1. Parses the PPM header.
2. Reads the image dimensions.
3. Loads RGB pixel data.
4. Creates an SDL2 window.
5. Renders each pixel.
6. Processes window events until exit.

---

## Project Structure

```text
PixView/
│
├── image_viewer.c
├── README.md
└── LICENSE
```

---

## Supported Formats

| Format | Status |
|--------|--------|
| PPM (P6) | Supported |
| PPM (P3) | Not supported |

---

## Limitations

- Supports only binary PPM (P6) images.
- Assumes a maximum colour value of 255.
- Images are rendered pixel-by-pixel.
- Accepts input only through standard input.
- Limited validation of malformed files.

---

## License

MIT License.
