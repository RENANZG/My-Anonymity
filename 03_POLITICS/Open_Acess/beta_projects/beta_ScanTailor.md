# How to Create an AppImage for ScanTailor

Follow these steps to create an AppImage for ScanTailor. ScanTailor is a post-processing tool for scanned books that helps improve the quality of scanned images.

# Scantailor
# https://github.com/4lex4/scantailor-advanced
# https://github.com/4lex4/scantailor-libs-build
# https://github.com/ScanTailor-Advanced/scantailor-advanced
# https://github.com/ScanTailor-Advanced/scantailor-libs-build


### Steps to Create an AppImage for ScanTailor

1. **Install the necessary dependencies**:

   ```bash
   sudo apt-get update
   sudo apt-get install -y git cmake g++ qt5-default qttools5-dev-tools libjpeg-dev libpng-dev zlib1g-dev libtiff-dev
   ```

2. **Clone the ScanTailor repository**:

   ```bash
   git clone https://github.com/4lex4/scantailor.git
   cd scantailor
   ```

3. **Compile ScanTailor**:

   ```bash
   mkdir build
   cd build
   cmake ..
   make
   ```

4. **Install AppImageTool**:

   ```bash
   wget https://github.com/AppImage/AppImageKit/releases/download/continuous/appimagetool-x86_64.AppImage
   chmod +x appimagetool-x86_64.AppImage
   ```

5. **Create the AppDir structure**:

   ```bash
   mkdir -p scantailor.AppDir/usr/bin
   cp scantailor scantailor.AppDir/usr/bin/
   ```

6. **Add an icon and a desktop file**:

   - Create a `scantailor.desktop` file inside `scantailor.AppDir` with the following content:

     ```plaintext
     [Desktop Entry]
     Name=ScanTailor
     Exec=scantailor
     Icon=scantailor
     Type=Application
     Categories=Graphics;
     ```

   - Add an icon to the `scantailor.AppDir` folder:

     ```bash
     mkdir -p scantailor.AppDir/usr/share/icons/hicolor/256x256/apps
     cp path/to/scantailor-icon.png scantailor.AppDir/usr/share/icons/hicolor/256x256/apps/scantailor.png
     ```

7. **Create the AppImage**:

   ```bash
   ./appimagetool-x86_64.AppImage scantailor.AppDir
   ```

### Final Result

The command above will generate an `.AppImage` file that can be run on any compatible Linux system. Now you have a ScanTailor AppImage that can be easily distributed and run without additional installation.

### References

- [AppImage Documentation](https://docs.appimage.org/)
- [ScanTailor GitHub Repository](https://github.com/4lex4/scantailor)
