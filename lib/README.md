# Building wxWidgets

## 📦 Description

This project serves as a minimal yet powerful starting point for building cross-platform **wxWidgets** GUI applications using **CMake**. It is designed to simplify the process of integrating wxWidgets into your application and ensure compatibility across Linux, macOS, and Windows.

---

## 🔧 Setting Up wxWidgets

To integrate and build wxWidgets locally in this project:

### 1. Download wxWidgets Source

- Visit the official wxWidgets download page:  
  👉 [https://www.wxwidgets.org/downloads/](https://www.wxwidgets.org/downloads/)
- Under **"Source for Linux, macOS, etc."**, click to download the full source archive (ZIP or TAR).

### 2. Extract into the Project

- Extract the downloaded wxWidgets folder.
- Move the extracted folder into your project’s `lib/` directory.
- Rename it to:

```
lib/wxWidgets/
```

This ensures the CMake script can find and build it as a subdirectory.


---

## 🧪 Troubleshooting

| Problem | Solution |
|--------|----------|
| `wxWidgets not found` | Ensure the extracted folder is correctly named `wxWidgets` and placed under `lib/`. |
| Build errors or missing headers | Run a clean build: delete `build/`, re-run CMake. |
| Missing CMake | Install via package manager (`sudo apt install cmake`, `brew install cmake`, or [cmake.org](https://cmake.org/download/)) |
| Linking errors | Make sure you’ve selected the correct configuration (Release or Debug) and the components needed are built. |

Still stuck? Visit the [wxWidgets documentation](https://docs.wxwidgets.org/) or their [support forums](https://discuss.wxwidgets.org/).

