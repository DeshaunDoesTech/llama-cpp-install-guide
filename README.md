# llama.cpp Installation Guide

By **DeshaunDoesTech**

A beginner-friendly guide to installing prebuilt llama.cpp tools on Windows, macOS, and Linux. This repository contains written instructions only: no program code, scripts, configuration files, or terminal commands.

[Support my tech guides on Buy Me a Coffee](https://buymeacoffee.com/DeshaunDoesTech)

## What is llama.cpp?

llama.cpp runs compatible AI models on your own computer. The engine and the model are separate downloads. It supports CPU execution and several GPU backends, including CUDA, Metal, Vulkan, and HIP.

**Scope:** This guide gets the prebuilt tools downloaded and unpacked. Running the native tools usually involves launch options in a terminal. Those commands are intentionally omitted. Downloading the files alone does not start a model or a chat website. Links to the official launch instructions are provided below.

## 1. Check your computer

1. Identify your operating system and processor architecture. On Windows 11, open **Settings → System → About** and inspect **System type**. On macOS, open **Apple menu → About This Mac**. On Linux, use your desktop's system information panel.
2. Distinguish x64 from ARM64. An AMD processor normally uses the x64 download; the word AMD does not mean ARM.
3. Identify your graphics hardware. On Windows, open **Task Manager → Performance** and select the GPU.
4. Check free disk space, system memory, and GPU memory. Models need storage plus working memory; their download size is not their total memory requirement.
5. Install current graphics drivers from your hardware manufacturer's official support site if you plan to use GPU acceleration.

## 2. Choose a download

Open the [official releases page](https://github.com/ggml-org/llama.cpp/releases). Prefer a stable release when one is available; prereleases and nightly builds may contain newer fixes and newer problems. Read the selected release's notes and expand **Assets** if necessary.

| Computer | Download to look for |
| --- | --- |
| Windows with an Intel or AMD x64 processor | Windows x64 CPU build, or a compatible GPU build |
| Windows on ARM | Windows ARM64 build, when supplied |
| NVIDIA GPU | CUDA build matching the platform and its listed runtime requirements |
| AMD or Intel GPU | Vulkan build when provided and supported by the installed driver |
| Apple Silicon Mac | macOS ARM64 build; Metal is the native GPU backend |
| Intel Mac | macOS x64 build |
| Linux PC | Linux build matching both processor architecture and distribution requirements |

For a Windows PC with a Radeon RX 9070 XT, a Windows x64 Vulkan package is a sensible starting point when offered. CUDA packages are for NVIDIA hardware. Actual acceleration still depends on the build, driver, and successful GPU detection.

Choose compiled binaries, not the **Source code** archives. Asset names and availability change, so follow the current labels rather than an old filename. If no compatible binary exists, consult the [official build guide](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md); compiling is outside this command-free guide.

## 3. Install on Windows 11

1. Download the chosen Windows archive from the official release.
2. In File Explorer, right-click the downloaded archive and select **Extract All**.
3. Choose a permanent folder you can easily find, such as a llama.cpp folder inside Documents.
4. Open the extracted folder, including its bin subfolder if present. Keep the executables and their supplied libraries together.
5. If the release lists a separate runtime package, download the matching package from that same release and follow its placement instructions.
6. Record the release tag and backend you chose for future troubleshooting.

This is a portable installation: unpacking the archive places the tools on your computer. A desktop shortcut or Start menu entry may not be created. Double-clicking a command-line executable may briefly open and close a console; that does not establish whether inference works.

## 4. Install on macOS

1. Download the macOS archive matching Apple Silicon or Intel.
2. Extract it with Finder's archive handling and keep the extracted files together in a permanent folder.
3. Review the release's macOS requirements before launching anything.
4. If macOS blocks a file, confirm its origin and consult Apple's guidance for that specific warning. Do not disable system security globally.

Native command-line binaries are not necessarily ordinary applications that you drag into Applications. The official installation documentation also describes package-manager alternatives, which require commands and are outside this guide.

## 5. Install on Linux

1. Read the chosen release's Linux or Ubuntu requirements. A build for Ubuntu is not a guarantee of compatibility with every distribution.
2. Download the matching architecture and backend archive.
3. Use your desktop's archive manager to extract it into a permanent user-owned folder.
4. Keep included libraries with the tools. Where your desktop supports it, inspect the executable's Properties or Permissions panel for permission to run it.
5. If a library or compatibility error occurs, use the release requirements and your distribution's documentation to resolve it. Do not copy arbitrary system libraries from download sites.

## 6. Download a model

1. Read the [official model guidance](https://github.com/ggml-org/llama.cpp/blob/master/docs/models.md).
2. Choose a llama.cpp-compatible GGUF model from a publisher you trust. For chat, choose an instruction-tuned or chat model.
3. Read its model card, license, hardware guidance, and any access conditions.
4. Open its files listing and download the chosen GGUF variant. Quantized variants reduce memory needs, with quality tradeoffs.
5. If the model is split into numbered parts, download all required parts of the same variant and keep their names intact in one folder.
6. Save models separately from the program folder so replacing the program does not remove them.

Start with a small model to verify the setup. Leave memory available for the operating system and context processing; GPU memory alone does not determine every model you can run.

## 7. Verify the installation and begin using it

Check that the archive extracted successfully, the expected tools and libraries are present, and your model download completed.

For an actual runtime test, follow the current [official quick start](https://github.com/ggml-org/llama.cpp#quick-start) and [server instructions](https://github.com/ggml-org/llama.cpp/tree/master/tools/server). These external pages contain commands. Select your model, start the appropriate tool, and confirm that the startup output reports the expected backend and loads the model without errors. Send a short test prompt and check for a response.

The built-in web interface is served by a running server; installing the binaries does not automatically open it. Use the local address reported by your server. Keep a personal test server local unless you deliberately configure network access and authentication.

## Troubleshooting

| Problem | What to check |
| --- | --- |
| Window closes immediately | The program may require terminal launch options; consult its official usage instructions. |
| Missing library | Re-extract the complete archive and check the release's runtime requirements. |
| GPU is not used | Confirm the backend, driver, detected device, and model offloading in startup output. |
| Model does not load | Verify GGUF compatibility, complete downloads, required split files, and sufficient memory. |
| Out of memory | Try a smaller model or quantization and reduce context length using the documented controls. |
| Old guide names differ from installed tools | Follow the documentation for your selected release; tool names and interfaces evolve. |

## Updating and removing

For updates, stop running tools, download a compatible newer release, and extract it into a new folder. Test before removing the previous version. Do not mix libraries from different releases. Keep your models and any settings you need.

For removal of this portable installation, stop the tools and remove their extracted folder and any shortcuts you created. Delete model downloads separately only if you no longer want them. Package-manager installations need that package manager's removal process.

## Support this guide

I create practical tech content on X and am expanding to more platforms. If this guide helps you, you can support future guides here:

**[Buy Me a Coffee — DeshaunDoesTech](https://buymeacoffee.com/DeshaunDoesTech)**

## License and sources

Copyright © 2026 DeshaunDoesTech. This original written guide is licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/). See [LICENSE.md](LICENSE.md).

This is an independent community guide. It does not redistribute or relicense llama.cpp or model weights. llama.cpp uses its own MIT license; each model retains its publisher's license.

Official references: [project](https://github.com/ggml-org/llama.cpp), [releases](https://github.com/ggml-org/llama.cpp/releases), [installation options](https://github.com/ggml-org/llama.cpp/blob/master/docs/install.md), [build and backend guidance](https://github.com/ggml-org/llama.cpp/blob/master/docs/build.md), [models](https://github.com/ggml-org/llama.cpp/blob/master/docs/models.md), and [server](https://github.com/ggml-org/llama.cpp/tree/master/tools/server).

Documentation reviewed November 10, 2026. Instructions were checked against official documentation; installation was not tested on each operating system.
