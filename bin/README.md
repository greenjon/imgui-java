### Overview

The folder contains libraries used by the binding and the `binding.sha1` checksum for the `imgui-binding/src/main` directory that the libraries are built upon. These libraries are utilized during the release process.

### Specifying the Library Path

To specify the folder containing these files, provide the `imgui.library.path` (or `java.library.path`) VM option. For example:
```
-Dimgui.library.path=./folder/path
```
You can also use the `java.library.path` option in the same manner.

### Changing the Library Name

By default, the binding expects the file name `imgui-java64`. You can change this by using the `imgui.library.name` VM option. For example:
```
-Dimgui.library.name=custom-lib-name.dll
```

### Expected Library File Names

The expected library file names for different operating systems are:

| OS      | Library               |
|---------|-----------------------|
| Windows | imgui-java64.dll      |
| Linux   | libimgui-java64.so    |
| Linux ARM64 | libimgui-java64-arm64.so |
| macOS   | libimgui-java64.dylib |

### Additional Information

- All libraries include statically compiled **FreeType**.
- `libimgui-java64-arm64.so` is the Linux aarch64 build. Its file name differs from the x86-64 one only because CI collects every platform into this single directory; when loading it by path, pass `-Dimgui.library.name=libimgui-java64-arm64.so`.
- The macOS version is a universal library and support x86_64 and arm64 architectures.

### Continuous Integration

The hash sum in the `binding.sha1` file is used in continuous integration (CI) to determine if there is a need to update the native binaries.
