# Resources:
https://opensource.com/life/16/10/introduction-linux-filesystems


# What's a file system in UNIX:
1) A physical storage:
      a) hard drives: HDD
      b) RAM:
            1. Energy-independent (SSD, USB stick)
            2. Energy-dependent (DDR*)

2) An OS level abstraction (/subtree/subtree/subtree)

3) Data storage format (EXT4, ZFS, BTRFS, XFS etc):
      is used for metadata (when files were created, howthey relate one to another, free space, namespace rules(max file name length, allowed characters etc))


# File System APIs

  API
  Kernel
  virtual FS
  Data storage format
  