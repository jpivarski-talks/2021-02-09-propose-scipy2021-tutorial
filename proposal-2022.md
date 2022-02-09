# Loopy and unloopy computing techniques

Contributors:

   * Jim Pivarski

## Short description

It's curious that Python is now the leading language for data analysis, since pure Python code is not fast and slow code × big data = long wait times. However, most number-crunching in scientific Python is performed in optimized, precompiled libraries: Python only directs the computation, steering it toward the user's intent. As a consequence, the most basic syntax one might learn in an introductory programming class—`if`, `for`, and `while`—are not what you should use when dealing with big data. You should use "vectorized" expressions, like slices, broadcasting, and array-at-a-time functions.

This tutorial is an introduction to vectorized array programming. Python beginners are welcome—any unfamiliar syntax will be minimized and explained as necessary—because the focus will be on _techniques_, rather than language or library features. It will be a guided tour through problems with loopy and unloopy solutions, using NumPy and Awkward Array for concreteness, but the techniques can be adapted to any array-oriented setting, such as GPU programming.

Tutorial prerequisites: basic familiarity with programming and evaluating code in Jupyter are helpful but not required. This tutorial "pairs well" with an introduction to NumPy or Pandas.

Setup instructions: none. We'll use cloud-based notebooks with everything preinstalled.

## Long description

Array-oriented programming is a paradigm in its own right, challenging its users to think about problems in a different way. Those users—from APL to scientific Python—are typically analyzing or simulating data. This tutorial will focus on the thought process: all of the problems will be solved both in an imperative (loopy) way and in a array-oriented (unloopy) way to fully explore the difference. Also, the problems are all data-centric: analyzing data or performing a simulation, with an eye toward scaling up the problems to big data.

The session will alternate between expositions of concepts and time-bound problems of about 20 minutes each. At the beginning of the session, in-person participants will be grouped in 3‒4 person teams to work on the problems together, and any online participants can be similarly grouped into Zoom break-out rooms. Each problem will have an optional extension to challenge advanced students/groups.

### Draft outline (subject to adaptation as problems are worked out and pre-tested):

**0:00‒0:10 (10 min)** Array-oriented programming as a paradigm: APL, SPEAKEASY, IDL, MATLAB, S, R, NumPy.

**0:10‒0:30 (20 min)** Arrays (single and multidimensional), element indexing, range slicing, boolean- and integer-array slicing, using text vectorization as an example.

**0:30‒0:40 (10 min)** Applying array-at-a-time (vectorized) functions to an array, multiple arrays (broadcasting).

**0:40‒1:00 (20 min)** **Exercise:** simulating waves. **Optional extension:** game of life.

**1:00‒1:10 (10 min)** _(break)_

**1:10‒1:30 (20 min)** "Iterate until converged" problem: computing a fractal.

**1:30‒1:50 (20 min)** **Exercise:** evaluating a decision tree, given the tree as an array. **Optional extension:** construct the array from a Python tree.

**1:50‒2:00 (10 min)** _(break)_

**2:00‒2:10 (10 min)** **Demo** mixing loopy and unloopy: computing the fractal (1) with a Numba kernel, (2) on a GPU.

**2:10‒2:20 (10 min)** Reducing dimensionality, using histogram-projection as an example.

**2:20‒2:40 (20 min)** **Exercise:** roll your own rolling mean. **Optional extension:** with a non-square kernel (e.g. Gaussian).

**2:40‒2:50 (10 min)** _(break)_

**2:50‒3:00 (10 min)** Irregularly shaped arrays (Awkward Arrays): indexing, slicing, and broadcasting with irregular arrays.

**3:00‒3:20 (20 min)** Chicago taxi trip dataset (Parquet file, variable number of trips per taxi and variable length paths per trip): basic exploration, putting techniques into practice (select by fare, by starting point in the city, etc.).

**3:20‒3:40 (20 min)** **Reduction exercise:** compute path lengths per trip. **Optional extension:** ratio of each with distance "as the crow flies."

**3:40‒4:00 (20 min)** **Bonus exercise:** tidy the data (put it in 3rd normal form), resulting in a table of taxis, a table of trips, and a table of positions in paths. **Optional extension:** repeat the calculation of path lengths per trip using "group by" in Pandas.

**Total time: 4 hours.**

asdf
