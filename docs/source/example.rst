**An Example**
==============

Here we provide an example for how to run the workflow.

Metagenomic study: ERP124921 Metaproteomics: PXD005780

1. Setting up the pipeline in your local machine, please follow the
   :doc:installation, then you should have a folder named as MetaPUF, in
   this folder, there are several subfolders, in the config folder,
   config.proteomics.yaml is the parameters that will be used in the
   pipeline, and the sample_info.csv file is the relationship table
   between the metaproteomics raw files and the metagenomics and/or
   metatranscriptomics assemblies, both of them are described in the
   :doc:inputs_outputs. In the resources folder, there are two protein
   reference fasta files, one contains the contaminat proteins and the
   other are the human reference proteomics, they are both described in
   our manuscript.

2. Downloading the files from the PRIDE archive to the folder that you
   set in the config.proteomics.yaml file, the parameter folder for the
   RAW input files are ``ThermoFold``, default value is ``input/Raw``,
   which means you should first create this folder in the working
   directory if you are downloading files to your local machine. After
   downloading the files, you will need to create subfolders for each
   sample, for example sample S6.raw, create a subfolder named ``S6``
   under the path of ``input/Raw``.

3. Creating the relationship table, since we have downloaded the MS raw
   files locally, we don’t need the column ``Raw file URLs`` anymore, we
   can left this column as blank but will need to keep the header. The
   column ``Sample`` is the name of the metaproteomics sample, also the
   name of the subfolder that we just created for each sample.
   ``Raw file`` is the raw file name that we downloaded from the PRIDE
   archive, ``Sample Accession`` and ``Assembly`` are the
   metagenomics/metatranscriptomoics information from ENA/MGnify. Since
   some metaproteomics sample has multiple
   metagenomics/metatranscriptomics asseblies, we need to duplicate some
   columns.

4. Please make sure the Proteomics analysis tools are all downloaded
   with the correct versions and paths. You will need to create
   subfolder ``workflow/bin`` under the working directory. And put the
   three tools there, with three seprate folders containing
   ThermoRawFileParser, SearchiGui and PeptideShaker.

5. Now, you can use the command line to run the pipeline, please go to
   the Snakemake environment first with ``conda activate snakemake`` if
   you have set this environment. Then just run the command
   ``snakemake --cores 4``. Because the whole pipeline runs quite long
   time, we suggest to use a job management tool to run the job remotely
   or run the job in background with screen command.

6. You can view the generated output files in the folders that described
   in :doc:
