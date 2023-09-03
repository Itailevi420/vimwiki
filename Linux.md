
## Linux Links

https://www.linux.com/topic/desktop/understanding-linux-links/
https://www.stackscale.com/blog/inodes-linux/

Links are a very handy way to create a shortcut to an original directory.
Links are used in many instances:
Sometimes to create a convenient path to a directory buried deep within
the file hierarchy;

other uses for links include:

- Linking libraries
- Making sure files are in constant locations (without having to move the original)
- Keeping a “copy” of a single file in multiple locations

# But aren’t these just “shortcuts”?


Let me explain. Say, for instance, you have an external drive, attached to
your Windows machine. On that drive is a folder called Music.
If you create a shortcut to the directory on your desktop, when you click to
open the shortcut, your file manager will open to the Music directory on your external drive.

Types of links
In Linux there are two different types of links:

Hard links

Symbolic links

The difference between the two are significant.

**hard links**, you can only link to files (and not directories);
you cannot reference a file on a different disk or volume, and they reference
the same inode as the original source. A hard link will continue to remain
usable, even if the original file is removed.

**Symbolic links**, on the other hand, can link to directories, reference a
file/folder on a different disk or volume, will exist as a broken (unusable)
link if the original location is deleted, reference abstract filenames and
directories (as opposed to physical locations), and are given their own, unique inode.


# TCP/Ip

