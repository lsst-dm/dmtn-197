.. image:: https://img.shields.io/badge/dmtn--197-lsst.io-brightgreen.svg
   :target: https://dmtn-197.lsst.io
.. image:: https://github.com/lsst-dm/dmtn-197/workflows/CI/badge.svg
   :target: https://github.com/lsst-dm/dmtn-197/actions/

#####################################
Streak Masking in DM Image Processing
#####################################

DMTN-197
========

Streaks caused by satellites are a persistent problem in optical images, and their occurrence will likely increase in the coming years. Many Hyper Suprime-Cam images are already affected by streaks, and the same is expected for Rubin Observatory data. In the LSST Data Release Production (DRP), most streaks and other artifacts are already detected and masked by the algorithm {{CompareWarpAssembleCoadd}}. However, some streaks are not caught at this stage and can contaminate the final coadds and detection catalogs. To find and mask these, we adopt a morphologically-based method for detecting streaks, which uses the Kernel-Based Hough Transform to detect straight lines. Once the lines are detected, the streak profile is fit and the affected portion of the image is masked out. This algorithm, {{maskStreaks}}, is included in the {{pipe_tasks}} package and is used in {{CompareWarpAssembleCoadd}} to remove streaks from coadds. Similar implementation in the Alert Production is possible but has not been implemented.


Links
=====

- Live drafts: https://dmtn-197.lsst.io
- GitHub: https://github.com/lsst-dm/dmtn-197

Build
=====

This repository includes lsst-texmf_ as a Git submodule.
Clone this repository::

    git clone --recurse-submodules https://github.com/lsst-dm/dmtn-197

Compile the PDF::

    make

Clean built files::

    make clean

Updating acronyms
-----------------

A table of the technote's acronyms and their definitions are maintained in the ``acronyms.tex`` file, which is committed as part of this repository.
To update the acronyms table in ``acronyms.tex``::

    make acronyms.tex

*Note: this command requires that this repository was cloned as a submodule.*

The acronyms discovery code scans the LaTeX source for probable acronyms.
You can ensure that certain strings aren't treated as acronyms by adding them to the `skipacronyms.txt <./skipacronyms.txt>`_ file.

The lsst-texmf_ repository centrally maintains definitions for LSST acronyms.
You can also add new acronym definitions, or override the definitions of acronyms, by editing the `myacronyms.txt <./myacronyms.txt>`_ file.

Updating lsst-texmf
-------------------

`lsst-texmf`_ includes BibTeX files, the ``lsstdoc`` class file, and acronym definitions, among other essential tooling for LSST's LaTeX documentation projects.
To update to a newer version of `lsst-texmf`_, you can update the submodule in this repository::

   git submodule update --init --recursive

Commit, then push, the updated submodule.

.. _lsst-texmf: https://github.com/lsst/lsst-texmf
