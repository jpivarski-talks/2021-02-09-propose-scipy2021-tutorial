# Starting conversations with Awkward data: A data-focused introduction to Awkward Arrays

Contributors:

   * Jim Pivarski

## Short description

There are a lot of great data analysis tools out there for rectilinear data: tables and grids of numbers. However, many real-life datasets are "awkward," containing nested JSON or variable-length lists. The Awkward Array library provides NumPy-like idioms for manipulating such data at large scales. This tutorial is an introduction to analysis with Awkward Array, putting the data first: most of the time will be spent drawing insights from real datasets, principally in small-group projects analyzing the Million Song dataset.

Topics will include element-wise math, advanced slicing with variable-length lists, nested and differently-shaped records, reducing structure with sum/min/max/any/all, creating structure with combinatorics and grouping, building new structures from scratch, and analyzing Awkward Arrays using traditional "for" loops in just-in-time compiled Numba.

Participants should be comfortable analyzing data with NumPy, Pandas, xarray, Matplotlib, or any tools built on these or similar to these. Basically, you should should be familiar with computing things "a whole array at a time" and basic plotting. No prior experience with Awkward Array or Numba will be assumed. All exercises will be presented in shared ("play along") Jupyter notebooks, and the small-group projects will be conducted in Zoom break-out rooms with intermittent help from the presenter.

## Long description

This tutorial will not be a comprehensive overview of Awkward Array, but we will learn Awkward Array features as needed to solve data-motivated problems. The datasets were chosen for breadth of subject matter while necessitating a non-rectilinear approach:

   * bike routes (GeoJSON) consist of variable numbers of variable-length paths, with lots of textual data supporting the numerical coordinates,
   * exoplanets (CSV) consist of a variable number of planets per star, and variable-sized data releases with nested structures representing asymmetric errors,
   * LHC collisions (ROOT) produce a variable number of electrons and muons in each event, from which the Higgs boson may be discovered,
   * Argo Floats (Parquet) measure temperature, pressure, and salinity at a variable number of ocean depths with a variable number of profiles each day,
   * the Million Song dataset (Parquet) contains detailed pitch and timbre samples, divided by notes, beats, and measures, over variable-length songs, rich in textual metadata.

The first hour of the tutorial will focus on exploratory data analysis with irregular structures, first in a presenter-led walk-through, then in a crowd-sourced exercise in which participants answer "What's the next step?" questions through a shared chat. (I have successfully been using Slido for this purpose, as participants can reinforce each other by upvoting solutions they agree with.)

The second hour will focus on scaling up and computing more complex quantities, with applications to the small-group projects in mind.

An hour and a half will be devoted to the small-group projects, which address various questions using the Million Song dataset. Such questions include

   * "Which musical intervals are common and which are not?"
   * Similarly for chords, sequences, and beat patterns.
   * "How do they correlate with metadata: artist keywords, country, and decade of release?"

I've already established that this dataset has many interesting patterns to be found (and they depend crucially on handling non-rectilinear data). The last half-hour is reserved for informal demos from each group about what they've accomplished. This goal of presenting "something interesting" gives participants a chance to share what they've learned and helps to focus the exploratory session on some kind of result, but without pressure.

### Draft schedule

**0:00-0:20 (20 min):** Introductory presentation: logistics, reminder of NumPy's arraywise mindset, and an overview of data types available in Awkward Array.

**0:20-0:40 (20 min):** Walk-through of exploratory data analysis (EDM) with the GeoJSON dataset. First with ufuncs and slices, then with Numba.

**0:40-1:00 (20 min):** All together (I ask questions, get responses in chat): exploratory analysis of the Exoplanets dataset.

**1:00-1:10 (10 min):** _(break)_

**1:10-1:20 (10 min):** Introduction to the Million Song dataset and example project questions (early, to get people thinking about it).

**1:20-1:40 (20 min):** Dealing with large-scale data: presenter-led walk-through of combinatorics for LHC mass peaks (including the Higgs discovery).

**1:40-2:00 (20 min):** All together: analyzing the Argo Floats dataset, including some non-trivial manipulations at large-scale.

**2:00-2:10 (10 min):** Break-out into small groups, including the logistics of finding people to work together on the same projects.

**2:10-3:30 (1 hour, 20 min):** Small groups work on their chosen Million Song projects. I cycle through break-out rooms to check on them, prioritizing any "calls for help."

**3:30-4:00 (30 min):** Each group informally demonstrates what they've accomplished.

## Setup instructions

Exact software requirements will be specified (with a test script) before the tutorial as part of the tutorial repository, though they will all be available on PyPI and conda-forge (`awkward`, `pyarrow`, `matplotlib`, JupyterLab, and possibly others). Python 3 will be required.

I will host public URLs to all the datasets used in the presentation, and I am looking into hosting cloud resources (Jupyter front-ends with direct access to the data) to give to participants for the duration of the tutorial. File sizes are:

   * 2.3 MB bike routes (GeoJSON)
   * 51 MB exoplanets (CSV)
   * 870 MB heavily prefiltered LHC collisions (ROOT)
   * 6.4 GB Argo Floats (Parquet) _or_ 0.7 GB subset (2020 only)
   * 79 GB Million Songs (Parquet) _or_ 0.7 GB subset (10,000 songs)

All participants will need to have access to the software and datasets, particularly the Million Songs (or its subset), to contribute to their group's data exploration. I'll know well in advance of the tutorial whether cloud resources will be available, which would remove the need for each participant to download the large files. (All are public datasets; I am in contact with most of those datasets' authors.)
