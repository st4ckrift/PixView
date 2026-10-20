<<<<<<< HEAD
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
=======
# Image Viewer

[![Language: C](https://img.shields.io/badge/language-C-A8B9CC.svg?logo=c&logoColor=white)](https://en.wikipedia.org/wiki/C_(programming_language))
[![Graphics: SDL2](https://img.shields.io/badge/graphics-SDL2-1d3557.svg)](https://www.libsdl.org/)
[![Platform: Linux](https://img.shields.io/badge/platform-Linux-1793d1.svg?logo=linux&logoColor=white)](https://www.linux.org/)
[![License: Unlicensed](https://img.shields.io/badge/license-unlicensed-lightgrey.svg)](#license)

A small C image viewer that reads a binary PPM (`P6`) image from standard input and displays it in an SDL2 window.

## Features

- Reads RGB pixel data from a `P6` PPM stream.
- Creates a window sized to the input image.
- Renders the image with SDL2 and keeps the window open until it is closed.
- Works with files, pipelines, and generated PPM output.

## Requirements

- A C compiler such as GCC or Clang.
- SDL2 development libraries and headers.
- A desktop environment capable of opening an SDL2 window.

### Install SDL2

Debian or Ubuntu:

```bash
sudo apt-get update
sudo apt-get install build-essential libsdl2-dev
```

macOS with Homebrew:
>>>>>>> 7320844 (Rewrite README for Image Viewer)

```bash
brew install sdl2
```

<<<<<<< HEAD
---
=======
Windows users can install SDL2 through [MSYS2](https://www.msys2.org/) or download the development libraries from [SDL's website](https://www.libsdl.org/).
>>>>>>> 7320844 (Rewrite README for Image Viewer)

## Build

Compile the viewer from the repository root:

```bash
<<<<<<< HEAD
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
=======
cc iv.c -o iv $(sdl2-config --cflags --libs)
```

If `sdl2-config` is unavailable, provide SDL2's include and linker flags directly. A typical Linux command is:

```bash
cc iv.c -o iv -lSDL2
```

## Usage

Pass a binary PPM image through standard input:

```bash
./iv < images.ppm
```

The repository includes `images.ppm` and `flower.ppm` as sample inputs:

```bash
./iv < flower.ppm
```

Other tools can be used to generate a PPM stream. For example, with ImageMagick:

```bash
convert input.jpg ppm:- | ./iv
```

Close the window to exit the application.

## Project Layout

| Path | Description |
| --- | --- |
| `iv.c` | SDL2 image viewer implementation |
| `images.ppm` | Sample PPM image |
| `flower.ppm` | Sample PPM image |
| `iv` | Prebuilt executable, when present |

## License

No license has been specified for this repository. Treat the source and bundled images as all rights reserved unless the project owner adds licensing terms.

## PPM Input Format

The viewer expects a binary `P6` PPM with this structure:

```text
P6
# optional comment
<width> <height>
255
<binary RGB pixel data>
```

Pixel bytes are read left to right, then top to bottom, as consecutive red, green, and blue values.

## Limitations

- Only binary `P6` PPM data is supported in practice. The magic number is currently read but not validated.
- The header parser expects the comment and header fields in fixed line positions.
- The maximum color value is assumed to be `255`.
- Malformed headers, truncated input, and SDL initialization errors are not reported robustly.
- Pixels are drawn individually with `SDL_FillRect`, so large images may render slowly.
- The complete image is read before the window becomes interactive.

## Development Ideas

- Validate the PPM magic number and all header fields.
- Support comments and whitespace according to the full PPM specification.
- Handle arbitrary maximum color values and truncated streams.
- Replace per-pixel surface fills with a texture or direct pixel buffer.
- Accept an image path as an optional command-line argument.
>>>>>>> 7320844 (Rewrite README for Image Viewer)
