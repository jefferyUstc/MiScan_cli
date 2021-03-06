Tutorial
================

Dependency data download
~~~~~~~~~~~~~~~~~~~~~~~~~~~

To predict breast cancer risk with MiScan, Users firstly needs to do:

* VCF Files

  We recommend using whole exon sequencing data to obtain individual variation
  information, but the results of whole genome sequencing and full-length RNA-seq
  data are also compatible with the model. Please download test VCF files from FTP_

* Maxout model weight

  Users also need a MiScan model weight to perform prediction, well-trained model weight can be downloaded from here_

usage-commandline
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Suppose your VCF file and weight are placed in the ``$dir`` directory, run with code::

    MiScan --vcf $dir/SRR5447191.combined.filtered.vcf -o outputs --weight $dir/_MiScan_weights.hdf5

or with below command::

    python -m MiScan --vcf $dir/SRR5447191.combined.filtered.vcf -o outputs --weight $dir/_MiScan_weights.hdf5


docker-commandline
~~~~~~~~~~~~~~~~~~~~~~~~~~~
if with docker, the path of VCF file or weight path shoule be path in Docker environment::

    docker run -v $dir_contains_VCF_MODEL_FILES:/miscan jefferyustc/miscan_command_line:latest \
     -o test_outputs --vcf sample.vcf --weight weights.hdf5

Attention: ``$dir_contains_VCF_MODEL_FILES`` should be a dir in your local system that contains sample vcf file and weight file


usage-script
~~~~~~~~~~~~~~~~~~~~~~~~~~~

users can also execute this from script::

    from MiScan import miscan_main
    miscan_main(
        outDir='./outputs',
        inVcf='/Users/jeffery/Downloads/SRR5447191.combined.filtered.vcf',
        model_weight='/Users/jeffery/workspace/projects/outputs/_MiScan_weights.hdf5'
    )



.. _FTP: http://galaxy.ustc.edu.cn:30803/MiScan/miscan_test_data/
.. _here: http://galaxy.ustc.edu.cn:30803/MiScan/miscan_model/MiScan_weight.h5