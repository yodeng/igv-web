## IGV-WEB

For deploy a web browser of IGV server.



#### Requirement

+ Linux
+ Python >=3.7



#### Install

```shell
git clone https://github.com/yodeng/igv-web.git
cd igv-web
conda create -n igvweb -c file://`pwd`/pkgs --offline igvweb 
```



#### Deployment

> step 1:  create a igvweb config

```shell
cat > ~/.igvweb.ini << EOF
[settings]
samtools = /share/data1/dengyong/soft/miniconda3/bin/samtools
tmpdir = /share/data3/dengyong/soft/igv-web/tmp

[genome]
fasta_hg19 = /share/data3/dengyong/soft/igv-web/db/hg19.fa
refgene_hg19 = /share/data3/dengyong/soft/igv-web/db/refGene.hg19.sorted.txt.gz
cytoband_hg19 = /share/data3/dengyong/soft/igv-web/db/cytoBand.hg19.txt
fasta_hg38 = /share/data3/dengyong/soft/igv-web/db/hg38.fa
refgene_hg38 = /share/data3/dengyong/soft/igv-web/db/refGene.hg38.sorted.txt.gz
cytoband_hg38 = /share/data3/dengyong/soft/igv-web/db/cytoBand.hg38.txt
fasta_other =
refgene_other =
cytoband_other =
EOF
```

> step 2:  apply migrations for igv

```shell
igvweb makemigrations
igvweb migrate
```

> step 3:  create super user for admin (optional)

```shell
igvweb createsuperuser
```

> step 4:  start your web

```shell
igvweb runserver IP:PORT
```

+ Open URL: `http://IP:PORT/` for starting IGV server



#### Download reference genome from UCSC

```
$ igvweb download -h

Download reference genome from ucsc, and make it used for igvweb.

optional arguments:
  -h, --help            show this help message and exit
  -g <str>, --genome <str>
                        hg19 or hg38 genome to download from ucsc, hg19 by default.
  -o <str>, --output <str>
                        output directory
  --version             show program's version number and exit
```



#### Soft Information and Effective Days

```
$ igvweb info

Igvweb Version: 1.0.0

Effective Days: 3 days

License File: /share/data1/dengyong/soft/miniconda3/envs/igv/lib/python3.9/site-packages/igvweb/license.lic

Configuration files to search (order by order):
 - /home/dengyong/.igvweb.ini
 - /share/data1/dengyong/soft/miniconda3/envs/igv/lib/python3.9/site-packages/igvweb/igvweb.ini

Available Config:
[settings]
 - samtools : /share/data1/dengyong/soft/miniconda3/bin/samtools
 - tmpdir : /share/data3/dengyong/soft/igv-web/tmp
[genome]
 - fasta_hg19 : /share/data3/dengyong/soft/igv-web/db/hg19.fa
 - refgene_hg19 : /share/data3/dengyong/soft/igv-web/db/refGene.hg19.sorted.txt.gz
 - cytoband_hg19 : /share/data3/dengyong/soft/igv-web/db/cytoBand.hg19.txt
 - fasta_hg38 : /share/data3/dengyong/soft/igv-web/db/hg38.fa
 - refgene_hg38 : /share/data3/dengyong/soft/igv-web/db/refGene.hg38.sorted.txt.gz
 - cytoband_hg38 : /share/data3/dengyong/soft/igv-web/db/cytoBand.hg38.txt
 - fasta_other : 
 - refgene_other : 
 - cytoband_other : 
```


#### Example

![20220726112522](https://user-images.githubusercontent.com/18365846/180916954-62ff1561-0331-4163-b7d7-33f50a1a1805.png)
![20220726112720](https://user-images.githubusercontent.com/18365846/180916964-d36ea56e-541b-445b-b915-94e8b6a36314.png)


#### Reference

[igvteam](https://github.com/igvteam)

#### Extra

This is only 10 effective days for experience.
