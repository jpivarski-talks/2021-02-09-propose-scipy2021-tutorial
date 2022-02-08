Because why should I make a new repo? Bha!

------

# Look ma, no for loops!

Contributors:

   * Jim Pivarski

## Short description

It's curious that Python is now the leading language for data analysis, since pure Python code is not fast and slow code × big data = long wait times. However, most number-crunching in scientific Python is performed in optimized, precompiled libraries: Python only directs the computational code, steering it toward the user's intent. As a consequence, the most basic syntax structures one might learn in an introductory programming class, "if", "for", and "while" loops, are not what you should use when dealing with big data. You should use "vectorized" expressions, like slices, broadcasting, and NumPy functions instead.

This tutorial is an introduction to vectorized data analysis techniques. It is aimed at beginners—very little Python will be assumed—
