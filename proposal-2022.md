# Loopy and unloopy data analysis techniques

Contributors:

   * Jim Pivarski

## Short description

It's curious that Python is now the leading language for data analysis, since pure Python code is not fast and slow code × big data = long wait times. However, most number-crunching in scientific Python is performed in optimized, precompiled libraries: Python only directs the computation, steering it toward the user's intent. As a consequence, the most basic syntax structures one might learn in an introductory programming class—`if`, `for`, and `while`—are not what you should use when dealing with big data. You should use "vectorized" expressions, like slices, broadcasting, and array-at-a-time functions.

This tutorial is an introduction to vectorized data analysis techniques. Python beginners are welcome—any unfamiliar syntax will be explained—but the focus will be on _techniques_, rather than language or library features. It will be a guided tour through problems with loopy and unloopy solutions, using NumPy, Pandas, and Awkward Array for concreteness, but the techniques can be adapted to any array-oriented setting, such as GPU programming.

Tutorial prerequisites: basic familiarity with Python/any other programming language, NumPy/Pandas/xarray, and evaluating code in Jupyter are helpful but not required.

Setup instructions: none. We'll use cloud-based notebooks with everything preinstalled.

## Long description

asdf
