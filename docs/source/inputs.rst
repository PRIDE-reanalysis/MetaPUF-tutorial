**Inputs and Outputs of MetaPUF**
=================================

This workflow offers the users to integrate publicly available
metagenomics, metatranscriptomics and metaproteomics datasets on PRIDE
and MGnify portals.

The workflow requires the following inputs in the
``config.proteomics.yaml`` file:

Mandatory inputs
----------------

-  ``Study`` : Under the ``parameters`` section, which takes in European
   Nucleotide Archive (ENA) secondary study accession: starts with
   (ERP|DRP|SRP) followed by six digits, e.g. ERP124921.

-  ``Input_dir/Pride_id``: Under the ``parameters`` section, one (only
   one) of them needs to be enabled. If you have the MS raw files
   available in your local machine, you can enable the ``Input_dir`` to
   give the path of the raw files as an input directory, or provide the
   PRIDE accession number if the raw files are publicaly available in
   PRIDE archive.

..

      We suggest downloading the raw files to your local machine and do
      the further analysis. Since the raw files downloading process
      usually takes a lot of time, and it will need to download from the
      beginning if the pipeline breaks when running.

-  ``Metadata``: Under the ``raws`` section, it is ``.csv`` file
   (defalut name: ``sample_info.csv``) which should be a relationship
   table between the metaproteomics raw files and the metagenomics
   and/or metatranscriptomics assemblies, this is mandatory as well
   because the data identifiers between PRIDE, MGnify and ENA are not
   related.

..

      Please make sure that the input metagenomics and/or
      metatranscriptomics assemblies and metaproteomics data are from
      the same samples.

-  ``.csv file``: which is the file mentioned in the ``Metadata``
   parameter contains all the sample information, please put this
   ``.csv`` file and the ``config.proteomics.yaml`` file in the same
   folder: ``config``.

An example for this file:

+----------+---------------+---------------+---------------+----------+
| Sample   | Raw file      | Raw file URLs | Sample        | Assembly |
|          |               |               | Accession     |          |
+==========+===============+===============+===============+==========+
| S6       | S6.raw        | https:        | ERS1509315    | ER       |
|          |               | //ftp.pride.e |               | Z1669330 |
|          |               | bi.ac.uk/prid |               |          |
|          |               | e/data/archiv |               |          |
|          |               | e/2017/07/PXD |               |          |
|          |               | 005780/S6.raw |               |          |
+----------+---------------+---------------+---------------+----------+

..

      You should leave the columns of the ``Raw file URLs`` as blank if
      you have the raw files locally, however the header is still
      needed.

Other input parameters
----------------------

The input parameters for the pipeline are all set in the
``config.proteomics.yaml`` file and you can change them based on your
own preferences. Some instructions regarding the parameters:

-  ``Version`` : The version of MGnify analysis. This accepts either
   “4.1” or “5.0” as string values. The default is “5.0”.

-  ``Db_size`` : Size of the proteins sequence database in bytes. This
   is mentioned in our manuscript, when the reference protein database
   is too large, the pipeline will apply a tree traversal algorithm to
   dynamically generate multiple Reference Search Databases based on the
   clusters of the samples. The default is 1073741824 (integer data
   type).

-  ``outputdir`` : Directory path to save the output

There are some other output folders for ``searchgui`` and
``peptideshaker``, the users can change the name themselves. Also, the
parameters in the ``searchgui`` section needs to be changed based on the
Mass spectrometry analysis.
