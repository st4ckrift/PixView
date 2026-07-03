# PPM Image Viewer (SDL2)

A minimal C program that reads a binary PPM (`P6`) image from **stdin** and displays it in a window using SDL2.

## How It Works

The program expects a PPM file piped in via standard input, structured like a standard `P6` PPM:

1. **Line 1** — Magic number (`P3`/`P6`). Read but ignored; the program assumes `P6` (binary RGB).
2. **Line 2** — Comment line. Read and discarded.
3. **Line 3** — Image dimensions (`width height`).
4. **Line 4** — Max color value (assumed to be `255`, not actually used).

After the header, it reads raw pixel data as consecutive `R G B` byte triplets, row by row, and draws each pixel into an SDL window surface using `SDL_FillRect`.

Once the whole image is drawn, the window stays open and processes events (handling window close) until the user quits.

## Requirements

- A C compiler (e.g. `gcc`)
- SDL2 development libraries

### Installing SDL2

**Debian/Ubuntu:**
```bash
sudo apt-get install libsdl2-dev
```

**macOS (Homebrew):**
```bash
brew install sdl2
```

**Windows:**
Install SDL2 via [MSYS2](https://www.msys2.org/) or download the development libraries from [libsdl.org](https://www.libsdl.org/).

## Building

```bash
gcc image_viewer.c -o image_viewer -lSDL2
```

> Replace `image_viewer.c` with the actual source filename.

## Usage

The program reads a PPM image from stdin, so pipe a `.ppm` file into it:

```bash
./image_viewer < image.ppm
```

You can also generate a PPM on the fly (e.g. using ImageMagick) and pipe it in:

```bash
convert input.jpg ppm:- | ./image_viewer
```

To close the viewer, click the window's close button (X).

## Notes & Limitations

- **Only `P6` binary PPM is truly supported.** The magic number line is read but not validated, so ASCII (`P3`) PPMs or other formats will produce garbage output or crash.
- **No error handling** for malformed headers, missing dimensions, or truncated pixel data.
- **Max color value is assumed to be 255.** Files with a different max value will not be scaled correctly.
- **Performance:** each pixel is drawn individually via `SDL_FillRect` in a nested loop, which is inefficient for large images. A locked-texture or direct pixel-buffer write would be faster.
- **Blocking read:** the image must be fully piped in before the window becomes interactive.
- Memory for temporary line buffers is allocated with `calloc` and freed after header parsing, but pixel-reading errors (e.g. EOF mid-image) are not checked.

## Potential Improvements

- Validate the magic number and reject non-`P6` input with a clear error.
- Support arbitrary max color values.
- Replace per-pixel `SDL_FillRect` calls with a locked texture / pixel buffer for performance.
- Add command-line argument support to read from a file path instead of only stdin.
- Add basic error handling for `fgets`/`getchar` failures and malformed headers.
