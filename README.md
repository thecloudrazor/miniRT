## LICENSE

- This project is licensed under the [**`Mozilla Public License 2.0`**](LICENSE).
- **You are under obligation** to comply with this license while interacting with this code, in any way, shape or form.
- As the creators of this project, we hereby declare that we grant complete authorization to all 42 Campus Administrators worldwide, to take any action they deem necessary in any occurrence of plagiarism, blind copying and/or cheating.
- We also hereby declare that we reserve all our rights to take legal action in any detectance of non-compliance to the license.

## Who's involved in this project?

- **Kuzey Berk YILMAZ** – [GitHub Profile](https://github.com/gm-infinite) – [Intra 42 Profile](https://profile.intra.42.fr/users/kuzyilma)
- **Emir İsmail GENÇ** – [GitHub Profile](https://github.com/thecloudrazor) – [Intra 42 Profile](https://profile.intra.42.fr/users/emgenc)

Please always feel free to reach out for any kind of collaboration ideas or questions.

# miniRT

miniRT is a minimal ray tracer project in C. It renders scenes which are fetched from inside a `.rt` file and makes use of diffuse shading, shadows and a single point light, all on top of the MiniLibX graphics library.

## Scene File Cheatsheet

Each non-empty line starts with an identifier followed by space-separated parameters:

| ID   | Meaning       | Parameters (comma = vector separator)     |
|------|---------------|-------------------------------------------|
| `A`  | Ambient light | ratio, color (R,G,B)                      |
| `C`  | Camera        | position, normalized dir, FOV (degrees)   |
| `L`  | Point light   | position, ratio                           |
| `sp` | Sphere        | position, diameter, color                 |
| `pl` | Plane         | position, normal, color                   |
| `cy` | Cylinder      | position, normal, diameter, height, color |

Vectors such as `0,0,1` use commas with no spaces. Ratios are clamped to `[0,1]`, FOV must stay inside `(0, 180)` and every number is validated via `ft_atof`.

## Repository Layout

- `rt.c`, `rt.h` – program entry point and global structures
- `parser*.c`, `parser.h` – tokenizer, validators and element dispatch
- `objects*.c`, `vector*.c`, `color*.c` – math primitives and object logic
- `draw_scene*.c`, `transformation.c` – ray casting, shading and helpers
- `e-libft/` – custom `libft` used across the project
- `maps/` – ready-to-run sample scenes

## Requirements

- POSIX compliant OS with build tools (`make` and `gcc`) and X11 (X server) installed.

## Build

```sh
git clone https://github.com/gm-infinite/miniRT.git
cd miniRT
make
```

`make clean/fclean/re` are available just like any other 42 project Makefile.

## Usage

```sh
./miniRT maps/sp.rt
```

- Press `Esc` or close the window to quit cleanly.
- Provide exactly one `.rt` file. Sample scenes live under the `maps/` directory.