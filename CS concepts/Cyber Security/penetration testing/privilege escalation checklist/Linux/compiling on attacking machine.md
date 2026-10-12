The issue you encountered is due to a **Glibc (GNU C Library) version mismatch** between your system and the victim system. Here's what happened:

1. **Different Glibc Versions**:  
   - When you compiled the program on your system, it was linked against the Glibc version installed on your machine.  
   - If the victim system has an older or incompatible version of Glibc, it won't be able to run the binary because it lacks the necessary symbols or features provided by the newer version.

2. **Dynamic Linking**:  
   - Most programs dynamically link to system libraries like Glibc at runtime. This means your program expects to find the same version of Glibc on the victim system as the one it was compiled with.  
   - If the version on the victim system is older or missing, the program fails with an error.

3. **Compiling on the Victim System**:  
   - When you compile the program directly on the victim system, it links against the version of Glibc available there, ensuring compatibility with that environment.

---

### Solutions to Fix This:

#### 1. **Static Linking**:
   - Compile your program with static linking to embed the necessary library code directly into the binary.
   - Use the `-static` flag during compilation:  
     ```bash
     gcc -static -o my_program my_program.c
     ```
   - **Pros**: The program becomes self-contained and doesn't rely on the victim system's Glibc.  
   - **Cons**: This results in a larger binary and may not work well with certain dynamic features or libraries.

#### 2. **Cross-Compile for the Victim System**:
   - Compile your program on your system but target the specific environment of the victim system using a cross-compiler or Docker container.
   - For example, if the victim system runs an older version of Glibc, you can use a container with that version to compile:
     ```bash
     docker run -v $(pwd):/src -it ubuntu:16.04 bash
     ```
     Inside the container:
     ```bash
     apt update && apt install -y gcc libc-dev
     gcc -o my_program /src/my_program.c
     ```

#### 3. **Ship the Required Libraries**:
   - Include the version of Glibc your program needs and set the `LD_LIBRARY_PATH` to use these libraries:
     ```bash
     export LD_LIBRARY_PATH=/path/to/custom/glibc:$LD_LIBRARY_PATH
     ./my_program
     ```
   - You can also use tools like [patchelf](https://github.com/NixOS/patchelf) to adjust the library paths in your binary.

#### 4. **Build on a Compatible System**:
   - Use the victim system to build the binary, as you did. Alternatively, use an older version of your development environment that matches the victim system's environment.

#### 5. **Use Portable Builds**:
   - Tools like [AppImage](https://appimage.org/) or [Flatpak](https://flatpak.org/) can package your application and its dependencies into a single portable file that runs across systems.

---

#### Debugging Tip:
To identify the Glibc version on a system, run:
```bash
ldd --version
```
Or check the dynamically linked libraries in your binary:
```bash
ldd my_program
```

By understanding the environment differences, you can ensure compatibility and avoid such issues.