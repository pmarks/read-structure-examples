# Example Read Structures for BAM &lt;-> FASTQ

This README shows a number of example datasets and their read structures for [hts-specs#270](https://github.com/samtools/hts-specs/issues/270).

### Required Background

See [Read Structures](https://github.com/fulcrumgenomics/fgbio/wiki/Read-Structures)

Note: if a sample barcode or molecular identifier is extracted from multiple reads, the bases are typically concatenated with a dash (`-`) delimiter.

### Dual-Index Fragment Run

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| i1.fq | index/i7 | `+B` | `BC` |
| i2.fq | index/i5 | `+B` | `BC` |
| r1.fq | read-one/R1 | `+T` | `SEQ` |

Example technology:: Illumina Standard

### Dual-Index Paired-End Run

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| i1.fq | index/i7 | `+B` | `BC` |
| i2.fq | index/i5 | `+B` | `BC` |
| r1.fq | read-one/R1 | `+T` | `SEQ` |
| r2.fq | read-two/R2 | `+T` | `SEQ` |

Example technology:: Illumina Standard

### Paired-End Run In-Line Sample Barcode

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| r1.fq | read-one/R1 | `10B+T`* | `BC` and `SEQ`|
| r2.fq | read-two/R2 | `+T` | `SEQ` |
* example has 10 bases of sample barcode in read-one

Example technology: Missing

### Paired-End Run i7 Sample Barcode and i5 Unique Molecular Identifier

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| i1.fq | index/i7 | `+B` | `BC` |
| i2.fq | index/i5 | `+M` | `RX` |
| r1.fq | read-one/R1 | `+T` | `SEQ` |
| r2.fq | read-two/R2 | `+T` | `SEQ` |
* example has 10 bases of sample barcode in read-one

Example technology: [NEBNext Direct](https://www.neb.com/nebnext-direct/nebnext-direct-for-target-enrichment)

### Paired-End Run In-Line and i7 Sample Barcode with In-line UMIs

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| i1.fq | index/i7 | `+B` | `BC` |
| r1.fq | read-one/R1 | `8B8M+T` | `BC`, `RX`, and `SEQ` |
| r2.fq | read-two/R2 | `8M+T` | `RX` and `SEQ` |

Example technology: [Riptide™ High Throughput Rapid Library Prep (HT-RLP)](https://igenomx.com/wp-content/themes/igenomx-wp-theme/docs/igenomx-product-overview-riptide.pdf)

### Dual-Index Paired-End Run with In-line Unique Molecular Identifiers and Skipped Bases

| FASTQ | Description | Read Structure | SEQ/Tags |
| --- | --- | --- | --- |
| i1.fq | index/i7 | `+B` | `BC` |
| i2.fq | index/i5 | `+B` | `BC` |
| r1.fq | read-one/R1 | `8M1S+T` | `RX`, **Discarded**, `SEQ` |
| r2.fq | read-two/R2 | `8M1S+T` | `RX`, **Discarded**, `SEQ` |

This is a good example of bases that are discarded and **not** present in the BAM

Example technology: [TwinStrand Biosciences Duplex Sequencing](http://www.twinstrandbio.com/duplex-sequencing/)