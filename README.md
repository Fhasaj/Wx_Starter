# wxWidgets Starter CMake Project Template

## Project Description

This project provides a foundation for creating **cross-platform wxWidgets applications** using **CMake**. It includes a well-organized directory structure, support for all major platforms (Linux, macOS, Windows), and out-of-the-box integration with wxWidgets components.

Use this template to quickly bootstrap GUI applications without worrying about build system details.

## Project Structure

```
MyWxApp/
├── CMakeLists.txt       # Main build configuration
├── headers/             # Your .h files
├── src/                 # Your .cpp files
├── lib/
│   └── wxWidgets/       # wxWidgets source code (CMake-enabled)
├── build/               
│   └── Debug/           # Where the Debug builds will be located
│   └── Release/         # Where the Release builds will be located
```

---

## What the CMakeLists.txt Does

- **Sets C++17 as the required standard**
- **Adds wxWidgets from a local subdirectory** (`lib/wxWidgets`) — assumes it's CMake-based
- **Finds and links to a wide set of wxWidgets components**, including GUI (`core`, `adv`, `aui`), rendering (`html`, `gl`), networking (`net`), and utilities (`xml`, `qa`)
- **Includes project-specific headers and sources from `headers/` and `src/`**
- **Generates an executable** named after the `project()` definition (default is `MyWxApp`)
- **Ensures compatibility across Windows, macOS, and Linux**, with consistent build behavior

---

## Building wxWidgets

To build wxWidgets, follow the instructions provided in the `lib/README.md`. Ensure wxWidgets is built before building your app, especially if you are linking against it locally.

---

## Building Instructions

You can build the project with CMake, todo so open the, `README.md` in either the `build/Debug` or `build/Release/`.

**Note:** After completing the Release build and verifying your output, feel free to delete the temporary `README.md` files inside `build/Release`.

---

## Running the Application

### Linux / macOS

```bash
./MyWxApp
```

### Windows

1. Navigate to `build\Debug\` or `build\Release\`
2. Double-click `MyWxApp.exe` in File Explorer

---

## Troubleshooting

### Linux

| Issue | Solution |
|-------|----------|
| CMake not found | `sudo apt install cmake` or `sudo pacman -S cmake` |
| Build files not generating | Check you're in the correct directory (`build/`) |
| Build failing | Check for missing system packages (e.g., GTK, OpenGL) |

### macOS

| Issue | Solution |
|-------|----------|
| CMake not found | `brew install cmake` |
| Build files not generating | Confirm `build/` exists and has write permissions |
| Build failing | Ensure dependencies like Xcode tools or wxWidgets are installed |

### Windows

| Issue | Solution |
|-------|----------|
| CMake not found | [Download CMake](https://cmake.org/download/) and add it to your PATH |
| Build files not generating | Ensure proper generator selected (e.g., `-G "Visual Studio 17 2022"`) |
| Build failing | Make sure dependencies like Visual Studio and wxWidgets are built correctly |

---

## License

© 2025 Fatlum Hasaj. All Rights Reserved.
