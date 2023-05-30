**Installation and usage**
==========================

The MetaPUF pipeline is built using
`Snakemake <https://snakemake.github.io/>`__, a workflow tool to create
reproducible and scalable data analyses. Below you can find tutorials on
what are the pre-requisites and how to use some of the MetaPUF pipelines
and standalones.

**Pre-requisites**
------------------

+---------------------+--------------------------+---------------------+
| Software            | Version                  | Purpose             |
+=====================+==========================+=====================+
| Python              | > 3.8                    | Snakemake is a      |
|                     |                          | Python based        |
|                     |                          | language            |
+---------------------+--------------------------+---------------------+
| Snakemake           | 7.3.8                    | Wrap the pipelines  |
+---------------------+--------------------------+---------------------+
| Conda(Miniconda)    |                          | We recommend to     |
|                     |                          | install Miniconda   |
|                     |                          | Python3             |
|                     |                          | distribution from   |
|                     |                          | `Miniconda <https:/ |
|                     |                          | /conda.io/en/latest |
|                     |                          | /miniconda.html>`__ |
+---------------------+--------------------------+---------------------+
| Bioconda            |                          | The pipelines in    |
|                     |                          | MetaPUF rely on     |
|                     |                          | third party         |
|                     |                          | software such as    |
|                     |                          | mg-toolkit that is  |
|                     |                          | not python          |
|                     |                          | libraries. We       |
|                     |                          | therefore recommend |
|                     |                          | to use conda that   |
|                     |                          | provides            |
|                     |                          | pre-compiled        |
|                     |                          | software for you    |
+---------------------+--------------------------+---------------------+
| Sourmash            | 4.4.2                    | Create DNA sketches |
|                     |                          | to group similar    |
|                     |                          | assemblies together |
+---------------------+--------------------------+---------------------+
| mg-toolkit          | 0.10.1                   | Pull information    |
|                     |                          | from MGnify web     |
|                     |                          | portal              |
+---------------------+--------------------------+---------------------+
| ThermoRawFileParser | 1.2.3                    | Convert Thermo Raw  |
|                     |                          | files into          |
|                     |                          | different formats   |
|                     |                          | of spectral files.  |
+---------------------+--------------------------+---------------------+
| Mono                | 6.12.0                   | Wrapper around the  |
|                     |                          | .net (C#),          |
|                     |                          | ThermoFisher,       |
|                     |                          | ThermoRawFileReader |
|                     |                          | library for running |
|                     |                          | on Linux            |
+---------------------+--------------------------+---------------------+
| SearchGUI           | 3.3.20                   | Combine multiple    |
|                     |                          | search engines to   |
|                     |                          | perform peptide     |
|                     |                          | identification from |
|                     |                          | a protein sequence  |
|                     |                          | database.           |
+---------------------+--------------------------+---------------------+
| PeptideShaker       | 1.16.45                   | Interpret           |
|                     |                          | proteomics          |
|                     |                          | identification      |
|                     |                          | results from        |
|                     |                          | multiple search and |
|                     |                          | generate peptide    |
|                     |                          | and protein         |
|                     |                          | reports.            |
+---------------------+--------------------------+---------------------+

**Installation**
----------------

-  **Create a conda environment**

We recommend to create a snakemake environment for the MetaPUF project,
you can find more details about how to install from
`here <https://snakemake.readthedocs.io/en/stable/getting_started/installation.html>`__,
after installation, please active the snakemake environment or you can
rename it.

::

   conda activate snakemake

-  **From Github source code**

You will need to install metapuf locally from Github

::

   git clone https://github.com/PRIDE-reanalysis/MetaPUF.git

-  **Options**

1. Please install (if you are using Linux/Mac OS)
   `Mono <https://www.mono-project.com/download/stable/#download-lin>`__
   for converting proteomics raw files. (install mono-complete if you
   encounter “assembly not found” errors).

2. Please add your project path to ``PYTHONPATH`` in your ``.bashrc``
   file:
   (i.e. ``export PYTHONPATH="/Users/your path/MetaPUF:$PYTHONPATH"``)

3. Please download the Proteomics tools (ThermoRawFileParser, SearchGUI,
   PeptideShaker, please find details in ``README`` in the project
   github page) and locate them in the correct folder
   (``MetaPUF/workflow/bin/``)

**Usage**
---------

Start running your own analysis with one line of code:

::

   snakemake --cores 4

..

   This is an example of running the workflow with Snakemake, we used 4
   cores, you should change it based on your own machine.

Also, it is recommended to test your pipeline before a real run, use a
snakemake dry run command:

::

   snakemake -np
