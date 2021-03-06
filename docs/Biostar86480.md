# Biostar86480

Genomic restriction finder


## Usage

```
Usage: biostar86480 [options] Files
  Options:
    -E, --enzyme
      restrict to that enzyme.
      Default: []
    -h, --help
      print help and exit
    --helpFormat
      What kind of help
      Possible Values: [usage, markdown, xml]
    -o, --output
      Output file. Optional . Default: stdout
    --version
      print version and exit

```


## Keywords

 * rebase
 * genome
 * enzyme
 * restricion
 * genome



## See also in Biostars

 * [https://www.biostars.org/p/86480](https://www.biostars.org/p/86480)


## Compilation

### Requirements / Dependencies

* java [compiler SDK 1.8](http://www.oracle.com/technetwork/java/index.html) (**NOT the old java 1.7 or 1.6**) and avoid OpenJdk, use the java from Oracle. Please check that this java is in the `${PATH}`. Setting JAVA_HOME is not enough : (e.g: https://github.com/lindenb/jvarkit/issues/23 )
* GNU Make >= 3.81
* curl/wget
* git
* xsltproc http://xmlsoft.org/XSLT/xsltproc2.html (tested with "libxml 20706, libxslt 10126 and libexslt 815")


### Download and Compile

```bash
$ git clone "https://github.com/lindenb/jvarkit.git"
$ cd jvarkit
$ make biostar86480
```

The *.jar libraries are not included in the main jar file, [so you shouldn't move them](https://github.com/lindenb/jvarkit/issues/15#issuecomment-140099011 ).
The required libraries will be downloaded and installed in the `dist` directory.

Experimental: you can also create a [fat jar](https://stackoverflow.com/questions/19150811/) which contains classes from all the libraries, on which your project depends (it's bigger). Those fat-jar are generated by adding `standalone=yes` to the gnu make command, for example ` make biostar86480 standalone=yes`.

### edit 'local.mk' (optional)

The a file **local.mk** can be created edited to override/add some definitions.

For example it can be used to set the HTTP proxy:

```
http.proxy.host=your.host.com
http.proxy.port=124567
```
## Source code 

[https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar86480.java](https://github.com/lindenb/jvarkit/tree/master/src/main/java/com/github/lindenb/jvarkit/tools/biostar/Biostar86480.java)


<details>
<summary>Git History</summary>

```
Thu Sep 7 15:26:22 2017 +0200 ; adding unit test with testng ; https://github.com/lindenb/jvarkit/commit/980b8937646e706a83b10f6b1ceeb015f37bbcc1
Wed May 24 17:27:28 2017 +0200 ; lowres bam2raster & fix doc ; https://github.com/lindenb/jvarkit/commit/6edcfd661827927b541e7267195c762e916482a0
Thu May 11 16:20:27 2017 +0200 ; move to jcommander ; https://github.com/lindenb/jvarkit/commit/15b6fabdbdd7ce0d1e20ca51e1c1a9db8574a59e
Fri Apr 7 16:35:31 2017 +0200 ; cont ; https://github.com/lindenb/jvarkit/commit/54c5a476e62e021ad18e7fd0d84bf9e5396c8c96
Sun Feb 2 18:55:03 2014 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/abd24b56ec986dada1e5162be5bbd0dac0c2d57c
Thu Nov 28 08:16:28 2013 +0100 ; cont ; https://github.com/lindenb/jvarkit/commit/d41deb4c340967592eb53e98101077ccbd84a3dd
Fri Nov 15 12:33:13 2013 +0100 ; vcf rebase ; https://github.com/lindenb/jvarkit/commit/a966b4adf21e22309466eaf84da60518bb078bf0
Fri Nov 15 00:53:11 2013 +0100 ; error in strand ; https://github.com/lindenb/jvarkit/commit/846fcad2dd6dfdc675e529403d47f9957edf4381
Thu Nov 14 22:20:43 2013 +0100 ; biostar 86480 ; https://github.com/lindenb/jvarkit/commit/8120514280e631ac4caca166e2d206d0ef9e5571
```

</details>

## Contribute

- Issue Tracker: [http://github.com/lindenb/jvarkit/issues](http://github.com/lindenb/jvarkit/issues)
- Source Code: [http://github.com/lindenb/jvarkit](http://github.com/lindenb/jvarkit)

## License

The project is licensed under the MIT license.

## Citing

Should you cite **biostar86480** ? [https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md](https://github.com/mr-c/shouldacite/blob/master/should-I-cite-this-software.md)

The current reference is:

[http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)

> Lindenbaum, Pierre (2015): JVarkit: java-based utilities for Bioinformatics. figshare.
> [http://dx.doi.org/10.6084/m9.figshare.1425030](http://dx.doi.org/10.6084/m9.figshare.1425030)


## Example
```bash
curl -s "http://hgdownload.cse.ucsc.edu/goldenPath/hg19/chromosomes/chr3.fa.gz" |\
gunzip -c  |\
java -jar dist/biostar86480.jar -E AarI -E EcoRI  

chr3	60645	60651	GAATTC	1000	+	EcoRI	G^AATTC
chr3	60953	60959	GAATTC	1000	+	EcoRI	G^AATTC
chr3	68165	68172	GCAGGTG	1000	-	AarI	CACCTGC(4/8)
chr3	70263	70269	GAATTC	1000	+	EcoRI	G^AATTC
chr3	70945	70952	GCAGGTG	1000	-	AarI	CACCTGC(4/8)
chr3	71140	71146	GAATTC	1000	+	EcoRI	G^AATTC
chr3	72264	72270	GAATTC	1000	+	EcoRI	G^AATTC
chr3	74150	74156	GAATTC	1000	+	EcoRI	G^AATTC
chr3	75063	75069	GAATTC	1000	+	EcoRI	G^AATTC
chr3	78438	78444	GAATTC	1000	+	EcoRI	G^AATTC
chr3	81052	81059	CACCTGC	1000	+	AarI	CACCTGC(4/8)
chr3	84498	84504	GAATTC	1000	+	EcoRI	G^AATTC
chr3	84546	84552	GAATTC	1000	+	EcoRI	G^AATTC
chr3	84780	84787	CACCTGC	1000	+	AarI	CACCTGC(4/8)
chr3	87771	87777	GAATTC	1000	+	EcoRI	G^AATTC
chr3	95344	95351	GCAGGTG	1000	-	AarI	CACCTGC(4/8)
chr3	96358	96364	GAATTC	1000	+	EcoRI	G^AATTC
chr3	96734	96740	GAATTC	1000	+	EcoRI	G^AATTC
chr3	105956	105962	GAATTC	1000	+	EcoRI	G^AATTC
chr3	107451	107457	GAATTC	1000	+	EcoRI	G^AATTC
(...)
```

