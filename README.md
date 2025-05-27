# wxWidgets Starter Cmake Project Template

## Project Description

This project provides a foundation for creating wxWidgets applications. It includes a basic structure and setup instructions to help you get started quickly.

## Building Instructions

### Common Steps

1. Open the file explorer and navigate to the `/lib` folder.
2. Read the `README.md` file in the `lib` folder for any specific instructions or dependencies.
3. Make sure you have CMake installed on your system. You can check by running `cmake --version` in the terminal.
4. Open a terminal and navigate to the root folder of the project.

### Building on Linux

1. Run the following command to generate the build files: `cmake -B build/linux .`
2. Once the build files are generated, run the following command to build the project: `cmake --build build/linux`
3. After the build is complete, you can find the executable file in the `build/linux` folder.

### Building on macOS

1. Run the following command to generate the build files: `cmake -B build/mac .`
2. Once the build files are generated, run the following command to build the project: `cmake --build build/mac`
3. After the build is complete, you can find the executable file in the `build/mac` folder.

### Building on Windows

1. Run the following command to generate the build files: `cmake -B build/windows .`
2. Once the build files are generated, run the following command to build the project: `cmake --build build/windows`
3. After the build is complete, you can find the executable file in the `build/windows` folder.

Note: If you are new to CMake or unsure about which build tool to choose, you can omit the `-G` flag and let CMake choose the default build tool for your system.

For more detailed instructions, please refer to the official wxWidgets documentation or consult the community resources.

## Running the Application

After building the project, you can run the executable file from the terminal or file explorer. The exact method may vary depending on your operating system and build configuration.

For example, on Linux, you can navigate to the `build/linux` folder and run the executable using the following command:

```
./wxwidgets_starter
```

On Windows, you can navigate to the `build/windows` folder and run the executable by double-clicking on it in the file explorer.

On macOS, you can navigate to the `build/mac` folder and run the executable using the following command:

```
./wxwidgets_starter
```

## Troubleshooting

If you encounter any issues while building the project, refer to the following tables for common issues and their solutions.

### Linux

| Issue | Solution |
|-------|----------|
| CMake not found | Install CMake using the package manager: `sudo apt-get install cmake` or `sudo pacman -S cmake` for arch users |
| Build files not generating | Ensure you're in the correct directory and try again |
| Build failing | Check the error message for any missing dependencies and install them |

### macOS

| Issue | Solution |
|-------|----------|
| CMake not found | Install CMake using Homebrew: `brew install cmake` |
| Build files not generating | Ensure you're in the correct directory and try again |
| Build failing | Check the error message for any missing dependencies and install them |

### Windows

| Issue | Solution |
|-------|----------|
| CMake not found | Download and install CMake from the official website |
| Build files not generating | Ensure you're in the correct directory and try again |
| Build failing | Check the error message for any missing dependencies and install them |

If you're still having issues, please refer to the official wxWidgets documentation or consult the community resources.
