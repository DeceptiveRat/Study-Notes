Mounting and symbolic links serve different purposes in Linux, and understanding the distinction is key to appreciating the role of mounts in the filesystem.

---

### **Why Mounting Is Necessary**
Mounting integrates a filesystem into the system's directory tree, allowing the data to be accessed as if it were part of the unified hierarchy. Here's what mounting changes:

1. **Access to the Filesystem**:
   - `/dev/sda13` represents the **raw block device**. Accessing it directly without mounting would give you raw binary data or blocks on the storage, not organized files and directories.
   - Mounting `/dev/sda13` at `/testfs` makes the contents of the ext2/ext3/ext4 filesystem stored on `/dev/sda13` accessible as a standard file and directory structure.

2. **Ease of Use**:
   - After mounting, you can interact with `/testfs` like any other directory in the hierarchy.
   - Without mounting, you’d need specialized tools (e.g., `dd` or `hexdump`) to interpret raw device data.

3. **Unified Namespace**:
   - Linux combines all mounted filesystems into a single hierarchical namespace, starting at `/` (the root filesystem).
   - Each mounted device appears as part of this tree, enabling seamless navigation and organization.

4. **Filesystem Operations**:
   - Mounting ensures that filesystem-specific drivers handle operations like reading and writing files, updating metadata, managing permissions, etc.
   - Without mounting, operations like file creation or deletion wouldn’t work, as raw devices lack this abstraction.

---

### **Mounting vs. Symbolic Links**
A **symbolic link** (`ln -s`) is just a shortcut or alias to another file or directory. It doesn’t affect how the system interprets or accesses the data.

1. **Symbolic Links**:
   - A symbolic link to `/dev/sda13` would simply provide another way to refer to the raw device.
   - Accessing the link (e.g., `cat /testfs`) would still give you raw binary data, not a usable filesystem.

   Example:
   ```bash
   ln -s /dev/sda13 /testfs
   cat /testfs  # Outputs raw binary data, not files or directories
   ```

2. **Mounting**:
   - Mounting `/dev/sda13` at `/testfs` makes the filesystem on `/dev/sda13` usable.
   - After mounting, `/testfs` acts like a normal directory containing files and subdirectories.

   Example:
   ```bash
   mount /dev/sda13 /testfs
   ls /testfs  # Outputs the files and directories stored in the filesystem
   ```

---

### **Why Mounting Adds Value**
- **Filesystem Structure**: Mounting interprets the binary data on the device according to the filesystem (e.g., ext2), allowing you to access files and directories.
- **Metadata Handling**: Mounting ensures that operations like permission checks, timestamps, and symbolic/ hard links are respected.
- **Device Independence**: You can mount various filesystems (ext4, FAT32, NTFS) on different directories and access them uniformly, regardless of the underlying device.

---

### **Practical Example**
1. **Without Mounting**:
   ```bash
   hexdump /dev/sda13  # Shows raw binary data
   ```
   Raw data isn't useful unless parsed manually.

2. **With Mounting**:
   ```bash
   mount /dev/sda13 /testfs
   ls /testfs  # Lists files and directories in the filesystem
   echo "Hello" > /testfs/hello.txt  # Creates a file on /dev/sda13
   ```

3. **Symbolic Link**:
   ```bash
   ln -s /dev/sda13 /testfs
   ls /testfs  # Will not show filesystem contents, only the symbolic link itself
   ```

---

### **Summary**
Mounting makes raw devices accessible as filesystems with organized files and directories. Symbolic links are shortcuts that don’t interpret raw device data or provide filesystem-level operations. By mounting, you unlock the ability to work with files and directories, which isn't possible with symbolic links or direct access to block devices.