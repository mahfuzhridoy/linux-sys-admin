# Sticky Bit in Linux

## 1. What is the Sticky Bit?

The Sticky Bit is a special Linux permission used mainly on directories that are shared by multiple users.  
When it is enabled, users can create files in the directory, but they cannot freely delete or rename files belonging to other users.  
For example, `/tmp` is commonly configured with the Sticky Bit because many users and applications need to create temporary files there.  
With the Sticky Bit enabled, deletion or renaming is generally restricted to the file owner, directory owner, or root.  
It is represented by a `t` in the directory's permission string, such as `drwxrwxrwt`.

## 2. Methods of Setting the Sticky Bit

The Sticky Bit can be enabled using the symbolic command:

chmod +t shared/

It can also be enabled using numeric permissions by adding `1000`:

chmod 1777 shared/

Its status can be checked with:

ls -ld shared/

A `t` at the end of the permission string indicates that the Sticky Bit is enabled. And if the t is a capital `T` then execution permission is not set.

## 3. Why Does a Linux Administrator Need to Know This?

The Sticky Bit becomes important when a directory is shared by multiple users.  
It allows users to create and work with their own files without allowing them to remove or rename files belonging to others.  
This makes it useful for directories such as `/tmp` and other shared working areas.  
Without appropriate protection, a user with write access to a shared directory could potentially delete another user's files.  
Understanding the Sticky Bit therefore helps administrators build safer and more predictable shared-directory permissions.