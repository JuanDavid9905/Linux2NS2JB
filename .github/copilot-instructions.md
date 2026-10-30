# Copilot Instructions: linux2ns2jb (Linux x86_64 AppImage Port)

## Target Architecture & System
- **Target OS:** Linux x86_64 (GCC / Clang)
- **Build System:** CMake & Make
- **Packaging Format:** Standalone AppImage (`linuxdeploy`)
- **Primary Dependencies:** `libusb-1.0`, `pkg-config`

## Porting & Code Rules
- **Strictly No macOS Code:** Completely strip out and replace all macOS-specific APIs, headers, or frameworks (such as IOKit, CoreFoundation, or Cocoa).
- **USB HID & Low-Level API:** Use standard `libusb-1.0` or raw Linux POSIX device nodes (`/dev/hidraw`, `/dev/bus/usb`) for USB HID communication and device control.
- **Network & Sockets:** Use standard POSIX sockets (`sys/socket.h`, `netinet/in.h`) for any network communication.
- **AppImage & CI Compatibility:** Ensure CMake supports proper installation targets (`make install DESTDIR=...`) so `linuxdeploy` can successfully bundle the binary, desktop entry, and icons into a clean AppImage on GitHub Actions (`ubuntu-latest`).
