# Avonix-OS

**Avonix-OS** is a custom, lightweight Debian-based Linux desktop intended for older laptops and everyday school, programming, office, and creative work. Its desktop uses a dark navy-and-cyan theme with a simple bottom panel and launcher.

## Design goals

- **Lightweight desktop:** Openbox window manager, Tint2 panel, Rofi application launcher, and PCManFM file manager instead of a large desktop environment.
- **Modern appearance:** Dark GTK styling, Papirus icons, custom wallpaper, and optional subtle effects through Picom.
- **Older-hardware focus:** Designed with systems such as an Intel Pentium 3825U laptop with 4 GB RAM in mind.
- **Low memory target:** Under 500 MB idle RAM is a goal to measure, **not a verified guarantee**. Actual usage depends on drivers, services, and the hardware.
- **Cloud ISO builds:** GitHub Actions builds the live ISO, so you do not need to install Docker or a Linux build environment on your Windows laptop.

## Applications included

Avonix-OS aims to bring together a web browser, Java programming tools, and lightweight creative applications. The build downloads the applications described below when their upstream Linux packages are available.

### 🌐 Thorium Browser

A Chromium-based web browser designed with performance in mind. Use it for websites, web apps, online learning platforms, and everyday browsing. The build script looks for an SSE4-compatible x86-64 release; compatibility depends on the CPU and the upstream release asset being available.

Project and releases: [Thorium releases](https://github.com/gz83/thorium/releases)

### ☕ BlueJ — Java learning and programming

BlueJ is an educational Java development environment, particularly useful for students learning object-oriented programming. It provides a straightforward workspace for creating Java classes, compiling and running programs, debugging code, and exploring class relationships visually.

Project and downloads: [BlueJ](https://www.bluej.org/)

### 🧰 Java Development Kit (JDK) 25

The build script attempts to install Eclipse Temurin JDK 25, the Java development toolkit. It includes the Java runtime and developer tools such as:

- **Java (java)** — runs Java applications.
- **Java compiler (javac)** — compiles Java source files into bytecode.
- **JAR tool (jar)** — creates and manages Java archive files.

The configured Java home is /opt/avonix/java. The exact upstream build available when the ISO is created determines the installed version. BlueJ compatibility with this JDK should be tested in the generated image.

### 📝 WordCraft — document writing

WordCraft is intended for writing and editing text documents, such as school assignments, notes, letters, and other written work. Its available formats and export options depend on the version of WordCraft included in the build.

Project and releases: [WordCraft releases](https://github.com/storytold/wordcraft/releases)

### 📊 DeckCraft — presentations

DeckCraft is intended for creating slide-based presentations for school projects, lessons, and demonstrations. Available templates, editing features, and export formats depend on the upstream release.

Project and releases: [DeckCraft releases](https://github.com/storytold/deckcraft/releases)

### 🎵 SoundCraft — audio creation

SoundCraft is intended for audio-focused creative work, such as working with recordings and arranging or editing sound. Audio production can use substantial CPU and memory, so complex projects may be demanding on a laptop with 4 GB RAM. Its exact capabilities depend on the upstream version included.

Project and releases: [SoundCraft releases](https://github.com/storytold/soundcraft/releases)

> **Application availability note:** These applications are obtained from upstream project sites or release assets during the ISO build. Upstream URLs and release filenames can change, so a build may need maintenance if an application publisher changes its download format. The presence of an application in this README describes the intended image configuration; verify the completed GitHub Actions build log and test the live ISO to confirm that each application installed and launches correctly.

## Lightweight desktop tools

The image also configures a set of basic desktop components and utilities:

- **Openbox** — lightweight window manager that controls application windows.
- **Tint2** — bottom panel for open windows and desktop shortcuts.
- **Rofi** — keyboard-friendly application launcher and command runner.
- **PCManFM** — file manager for browsing folders and files.
- **LXTerminal** — terminal for running command-line tools.
- **Mousepad** — simple text editor for notes and configuration files.
- **NetworkManager** — network connection management.
- **Picom** — compositor configured to use the XRender backend for modest visual effects.
- **zram-tools** — compressed RAM swap support to help when memory is limited.
- **Audio utilities and fonts/icons** — supporting desktop packages for sound and appearance.

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| Super + Space | Open application launcher |
| Super + E | Open file manager |
| Super + T | Open terminal |
| Super + R | Run a command |
| Super + D | Show desktop |
| Alt + F4 | Close the active window |

## Build the ISO with GitHub Actions

1. Open the repository's **Actions** tab.
2. Select **Build Avonix-OS ISO**.
3. Choose **Run workflow** on the main branch.
4. Wait for the workflow to finish successfully.
5. Download the **Avonix-OS-ISO** artifact from the completed run.
6. Use the included SHA-256 checksum file to verify the downloaded ISO.

The workflow uses a temporary container on GitHub-hosted infrastructure to build the Debian Live image. Docker is used on the cloud runner, not on your laptop.

## Testing and safety notes

- The project targets older hardware, including the HP 15-series laptop with an Intel Pentium 3825U, 4 GB RAM, and a 500 GB hard drive.
- The ISO is intended to start as a live session and does not modify Windows merely by being downloaded or built.
- Test the live session and check Wi-Fi/Ethernet, audio, display, suspend, and application launches before considering installation.
- Back up important files before changing disk partitions or installing any operating system.
- The under-500 MB idle-RAM goal, app compatibility, and performance have **not been verified until tested on the target laptop**.
