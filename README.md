# Make_an_empty_repository_on_GitHub
Adding a note about collaboration.

def add(a, b):
    """
    Adds two numbers together.

    Parameters:
    a (int or float): The first number.
    b (int or float): The second number.

    Returns:
    int or float: The sum of the two numbers.
    """
    return a + b

    #################################################################################
# Run snpEff annotation on per-strain VCF files using GNU parallel. Provides
# parallel processing of VCF files for efficiency
#
# Usage: bash run_snpeff.sh <output_dir> <num_jobs> <input_dir>
#
# Expects:
#   <input_dir>/<strain>.vcf                — VCF files
#   <input_dir>/snpeff_dbs/snpeff.config    — database config
#   
#
# Produces:
#   <output_dir>/variants/<strain>.ann.vcf   — annotated VCF
#################################################################################


#!/bin/bash
GFF_DIR="/path/to/gff_files"

for gff_file in "${GFF_DIR}"/*.gff; do
    cds_count=$(awk -F'\t' '$3=="CDS"' "$gff_file" | wc -l)
    echo "$gff_file has $cds_count CDS features"
done

#!/bin/bash
READS_DIR="/path/to/reads"
OUT_DIR="/path/to/qc_reports"
THREADS=4

mkdir -p "$OUT_DIR"

for r1 in "${READS_DIR}"/*_R1.fastq.gz; do
    r2="${r1/_R1/_R2}"
    fastqc -t "$THREADS" -o "$OUT_DIR" "$r1" "$r2"
done