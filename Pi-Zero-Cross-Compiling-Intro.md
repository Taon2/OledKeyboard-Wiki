This is intended currently as a rough intro to compile to the pi. This assumes everything else is setup


1. Install CLion. You can get a license for jetbrains for free with you
2. Clone the repo: https://dev.azure.com/MSOE2022SeniorDesignProjects/OLED_Keyboard/_git/DemoCode
3. Open it in clion
4. Goto Settings -> Build, Execution, Development -> Toolchains
5. Create a new WSL toolchain. Make it look like below
![image.png](/.attachments/image-fd3ed5ae-de5d-44c0-89e8-9e863ace688f.png)
6. Goto CMake
7. Paste `-DCMAKE_TOOLCHAIN_FILE="../Toolchain-rpi.cmake"` into the CMake Options box like below
![image.png](/.attachments/image-a2ae19dd-a541-49f2-8a1e-1084958751b2.png)
8. Make sure it uses WSL for PI toolchain

You should be able to compile on your machine then throw it to the Pi using sftp or gdb. DM me if you need more info.