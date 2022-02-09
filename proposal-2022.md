# Loopy and unloopy programming techniques

Contributors:

   * Jim Pivarski

## Short description

It's curious that Python is now the leading language for scientific computing, since pure Python code is not fast and slow code × big data = long wait times. However, most number-crunching in Python is performed by optimized, precompiled libraries: Python only directs the computation, steering it toward the user's intent. As a consequence, the most basic syntax you might learn in an introductory programming class—`if`, `for`, and `while` loops—is not what you should use when dealing with big data. You should use "vectorized" expressions, like slices, broadcasting, and reducers.

This tutorial is an introduction to vectorized array programming. Python beginners are welcome—unfamiliar syntax will be minimized and explained as necessary—because the focus is on _techniques_, rather than language or library features. It is a guided tour through problems with loopy and unloopy solutions, using NumPy and Awkward Array for concreteness, but the techniques can be adapted to any array-oriented setting, such as GPU programming (demo included).

**Tutorial prerequisites:** familiarity programming in any language, or mathematical thinking in general, would be helpful.

**Setup instructions:** none. We'll use cloud-based notebooks with everything preinstalled.

## Long description

Array-oriented programming is a paradigm in its own right, challenging its users to think about problems in a different way. From APL in 1966 to NumPy today, those users are typically scientists analyzing or simulating data. This tutorial focuses on the thought process: all of the problems are to be solved both in an imperative (loopy) way and in a array-oriented (unloopy) way to fully explore this distinction. Also, the problems are all data-centric: analyzing data or performing a simulation, with an eye toward scaling up the problems to big data. Matplotlib will be used for plotting, but all plotting commands will be given (not prerequisites).

The session alternates between expositions of concepts and time-bound problems (about 20 minutes each). At the beginning of the session, in-person participants will be grouped in 3‒4 person teams to work on the problems together, and any online participants can be similarly grouped into Zoom break-out rooms. Each problem will have an optional extension to challenge advanced students/groups.

### Draft outline (subject to adaptation as problems are worked out and pre-tested):

**0:00‒0:10 (10 min):** Array-oriented programming as a paradigm: APL, SPEAKEASY, IDL, MATLAB, S, R, NumPy. (Showing the keyboard APL used!)

**0:10‒0:30 (20 min):** Arrays (single and multidimensional), element indexing, range slicing, boolean- and integer-array slicing, using text-vectorization as an example. (Powerful concept: element indexing is function application, and integer-array slicing is function composition.)

**0:30‒0:40 (10 min):** Applying array-at-a-time (vectorized) functions to an array and multiple arrays (with a word about broadcasting).

**0:40‒1:00 (20 min):** **Exercise:** simulating waves in a fluid. I'll explain how to compute a time-step; the problem will be to apply it to all pixels iteratively (with loops and without loops). **Optional extension:** implement Conway's game of life in a similar way.

**1:00‒1:10 (10 min):** _(break)_

**1:10‒1:30 (20 min):** The "iterate until converged" problem, using a Mandelbrot calculation as an example.

**1:30‒1:50 (20 min):** **Exercise:** evaluating a decision tree for many inputs at once (given the tree as an array of indexes pointing to the next nodes). Leaves have to be absorbing states; iteration stops when all inputs reach leaves. **Optional extension:** instead of the busy-wait, try masking out the inputs that have reached leaves. Which method is faster (for a set of example trees)?

**1:50‒2:00 (10 min):** _(break)_

**2:00‒2:10 (10 min):** **Demo** mixing loopy and unloopy code: computing the Mandelbrot (1) with a Numba kernel for each pixel, (2) parallelized over pixels, and (3) on a GPU.

**2:10‒2:20 (10 min):** Using reducers, with histogram-projection (sum 3D → 2D and 2D → 1D) as an example.

**2:20‒2:40 (20 min):** **Exercise:** roll your own rolling mean (without `np.convolve` or `pd.DataFrame.rolling`). **Optional extension:** do it with a non-square kernel (e.g. a Gaussian kernel).

**2:40‒2:50 (10 min):** _(break)_

**2:50‒3:00 (10 min):** Introducing irregularly shaped arrays, with the Awkward Array package: indexing, slicing, and broadcasting with irregular arrays.

**3:00‒3:20 (20 min):** Chicago taxi trip dataset (~GB Parquet file, variable number of trips per taxi and variable length paths per trip): basic exploration, putting techniques into practice (select by fare, by starting point in the city, by starting date, etc.).

**3:20‒3:40 (20 min):** **Reduction exercise:** compute path lengths per trip. **Optional extension:** find the ratio of each with distance "as the crow flies."

**3:40‒4:00 (20 min):** **Bonus exercise:** tidy the data (put it in 3rd normal form), resulting in a table of taxis, a table of trips, and a table of positions in paths. **Optional extension:** repeat the calculation of path lengths per trip using "group by" in Pandas.

**Total time: 4 hours.**

All of the exercises are break-out sessions. If in-person, I would walk around the room, checking up on each group. If on Zoom, I would navigate between break-out room. (If hybrid, I can do both.) The exposition parts are all together, following prepared examples, but allowing for questions. The one demo (at **2:00**) is exposition—whether the students will be able to try it with me depends on whether I manage to get cloud resources with GPUs attached. If not, we'll be using mybinder.org without GPUs; they'll only be able to watch.
