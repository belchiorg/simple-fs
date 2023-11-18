# simple-fs
### Project built for Operating Systems class.

TecnicoFS is a user-mode file system designed with simplicity in mind, offering a straightforward interface for file operations. The project comprises a fundamental file system structure, complemented by additional functionalities introduced.

## Base Project Highlights

TecnicoFS establishes a foundation for file system management with the following key aspects:

- **File System Structure:**
  - Inode tables and a dedicated data region are utilized to organize the file system state.
  - The open file table efficiently tracks opened files along with their cursor positions.

- **Simplifications:**
  - A single-root directory ("/") governs the file system, containing files but no subdirectories.
  - Content within files and the root directory is constrained to a single block.
  - The system caters to a single client process, devoid of access control measures.
  - The implementation currently lacks thread safety and does not persist data structures in secondary memory.

## Exercise 1 Expansions

### 1.1 Copy from External File System

The introduction of the `tfs_copy_from_external_fs` function enables the seamless importation of external files from the host operating system into TecnicoFS.

### 1.2 Alternative Names and Shortcuts

- **Hard Links (Alternative Names):**
  - By implementing the `tfs_link` function, TecnicoFS supports the creation of hard links. These links involve adding entries in different directories that point to the same inode, allowing for alternative names for files.

- **Soft Links (Shortcuts):**
  - TecnicoFS facilitates the creation of soft links through the `tfs_sym_link` function. Soft links store references to file names, offering convenient shortcuts for accessing files.

- **Deletion:**
  - The `tfs_unlink` function empowers users to delete files and links, maintaining system integrity.

### 1.3 Support for Concurrent Calls

TecnicoFS has been enhanced to accommodate concurrent execution by multiple client tasks. Achieved through the implementation of thread-safe mechanisms, the system now utilizes logical locks (`pthread_mutex`) or read-write locks (`pthread_rwlock`).

### Source code

Check the source code [here](https://github.com/tecnico-so/projeto-so-2022-23/tree/ex1)
