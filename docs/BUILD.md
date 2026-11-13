# Building UwU Dimension

The project already includes its Minecraft and NeoForge build configuration in `build.gradle`:

- Minecraft 1.21.1, through NeoForge 21.1.249
- NeoForge ModDev Gradle plugin 2.0.148
- Java 21
- Gradle Wrapper 9.2.1 (`gradle/wrapper/gradle-wrapper.properties`)

On first build, the Gradle wrapper downloads Gradle and the NeoForge ModDev plugin downloads the matching Minecraft/NeoForge compile artifacts. These generated game libraries should not be committed to this repository.

From the project root, run `./gradlew jar` on Linux/macOS or `gradlew.bat jar` on Windows. The distributable is written to `build/libs/`. The `gradlew` script must retain its executable bit in Git for Linux and GitHub Actions builds.

The `libs/` folder is not required to package the mod JAR. `build.gradle` resolves the compile-time Simply Swords and Architectury dependencies, and uses the CurseMaven Another Furniture artifact when its local JAR is absent. `ci/get-mods.sh` downloads the checksum-pinned profile JARs into `libs/` for the fuller development client and expedition workflows; it is not part of the basic `jar` task.

The resulting mod still has its existing runtime dependencies listed in `UwU-Dimension-README.md` and `src/main/resources/META-INF/neoforge.mods.toml`.
