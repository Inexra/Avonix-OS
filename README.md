# Avonix-OS

A custom, lightweight Debian-based Linux desktop designed for older laptops, including Intel Pentium-class CPUs and 4 GB RAM systems.

## Goals

- Clean, modern dark navy / cyan desktop with a bottom dock-like panel.
- Openbox instead of a heavy desktop environment; Picom uses XRender for modest effects.
- Target idle memory usage below 500 MB. This is a **measurement target, not a guarantee**; actual usage depends on hardware, drivers, services and running apps.
- Bootable hybrid ISO built by GitHub Actions. No local Android Studio or Docker installation is required.

## Included applications

- **Thorium Browser** — release asset selected dynamically from the Thorium GitHub release API, using its SSE4 build for compatible x86-64 CPUs.
- **BlueJ** — downloaded from its official Linux download page.
- **Java Development Kit 25** — latest GA Eclipse Temurin JDK 25 at build time, with `JAVA_HOME=/opt/avonix/java`.
- **WordCraft** — latest x86_64 AppImage from [storytold/wordcraft](https://github.com/storytold/wordcraft/releases).
- **DeckCraft** — latest x86_64 AppImage from [storytold/deckcraft](https://github.com/storytold/deckcraft/releases).
- **SoundCraft** — latest x86_64 AppImage from [storytold/soundcraft](https://github.com/storytold/soundcraft/releases).

These native Craft apps are substantial and increase ISO size and their own runtime memory needs. Their download links are selected from official GitHub release assets.

## Desktop shortcuts

- `Super + Space` — application launcher
- `Super + E` — file manager
- `Super + T` — terminal
- `Super + R` — run command
- `Super + D` — show desktop
- `Alt + F4` — close window

## Build the ISO

1. Open the **Actions** tab.
2. Select **Build Avonix-OS ISO**.
3. Click **Run workflow** on the `main` branch.
4. After a successful run, download the `Avonix-OS-ISO` artifact.
5. Verify the image using the included SHA-256 file.

The workflow runs Debian Live Build inside a temporary container on GitHub-hosted infrastructure. Docker is used only in GitHub Actions, not on your laptop.

## Important notes

- This is an installer-free live ISO; it does not modify the existing Windows installation by itself.
- Test the live session and hardware compatibility before installing. Back up important files before any disk installation.
- App releases and upstream download URLs can change. The build is intended to fail with logs if a required app cannot be retrieved.
- Java 25 is installed separately from BlueJ; test their compatibility in the generated image.
- The under-500 MB idle RAM target must be measured on the target laptop; it is not claimed as verified yet.
