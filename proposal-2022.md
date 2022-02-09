# Loopy and unloopy data analysis techniques

Contributors:

   * Jim Pivarski

## Short description

It's curious that Python is now the leading language for data analysis, since pure Python code is not fast and slow code × big data = long wait times. However, most number-crunching in scientific Python is performed in optimized, precompiled libraries: Python only directs the computation, steering it toward the user's intent. As a consequence, the most basic syntax structures one might learn in an introductory programming class—`if`, `for`, and `while`—are not what you should use when dealing with big data. You should use "vectorized" expressions, like slices, broadcasting, and array-at-a-time functions.

This tutorial is an introduction to vectorized data analysis techniques. Python beginners are welcome—any unfamiliar syntax will be minimized and explained as necessary—because the focus will be on _techniques_, rather than language or library features. It will be a guided tour through problems with loopy and unloopy solutions, using NumPy, Pandas, and Awkward Array for concreteness, but the techniques can be adapted to any array-oriented setting, such as GPU programming.

Tutorial prerequisites: basic familiarity with programming and evaluating code in Jupyter are helpful but not required. This tutorial "pairs well" with an introduction to NumPy or Pandas.

Setup instructions: none. We'll use cloud-based notebooks with everything preinstalled.

## Long description

Array-oriented programming is a paradigm in its own right, challenging its users to think about problems in a different way. Those users—from APL to scientific Python—are typically data analysts. This tutorial will focus on the thought process: all of the problems will be solved both in an imperative (loopy) way and in a array-oriented (unloopy) way to fully explore the difference. Also, the problems are all data-centric: starting with a dataset and deriving some conclusion from it.

The general organization alternates between exposition of concepts and short, time-bound problems of about 10 minutes each. At the beginning of the session, in-person participants will be grouped in ~3 person teams to work on the problems together, and any online participants can be similarly grouped into Zoom break-out rooms. Each problem will have an optional extension to challenge advanced students/groups.

**Draft outline** (subject to adaptation as problems are worked out and pre-tested):


