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
| SearchGUI           | 4.0.41                   | Combine multiple    |
|                     |                          | search engines to   |
|                     |                          | perform peptide     |
|                     |                          | identification from |
|                     |                          | a protein sequence  |
|                     |                          | database.           |
+---------------------+--------------------------+---------------------+
| PeptideShaker       | 2.0.33                   | Interpret           |
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

-  **Add bioconda channels**

When you want to install a ny package, conda looks on the official
Anaconda website (channel). However many channels are present, we will
use bioconda channel. To use this type the command:

::

   conda config --add channels defaults
   conda config --add channels bioconda

It is important to have the channels in the right order. You can check
the `order <https://bioconda.github.io/>`__ with the command

::

   conda config --get channels

-  **Create a conda environment**

Once miniconda is installed and the channels set, you can create a new
environment for MetaPUF using the command

::

   conda env --name metapuf create --f metapuf_env.yml

You must active the metapuf environment whenever you work with this
workflow.

::

   conda activate metapuf

-  **From Github source code**

You can install metapuf locally from Github

::

   git clone https://github.com/PRIDE-reanalysis/MetaPUF.git

**Usage**
---------

Start running your own analysis with one line of code:

::

   snakemake --cores 4

..

   This is an example of running the workflow with Snakemake, we used 4
   cores, you should change it based on your own machine.

ALso, you can test your pipeline before a real run, use a Snakemake dry
run command:

::

   snakemake -n --cores 4
