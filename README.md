# project1-sequence-analysis
Python analysis of nucleotide mismatches in fission yeast sequencing reads, comparing genotoxic treatment and control samples.
DNA Sequence Mismatch Analysis

Title and Purpose

This Python project identifies nucleotide mismatches in Schizosaccharomyces pombe sequencing reads to investigate differences in mismatch frequencies, substitution patterns and positions between genotoxic agent-treated and untreated samples.

How to Run the Program

Open the project notebook in Google Colab and run the cells sequentially. The setup code automatically downloads the required files. The final analysis section generates sample summaries and statistical comparisons.

Inputs and Outputs

The program uses reference.txt, containing a 200-nucleotide reference sequence, and reads.csv, containing 6,000 sequencing reads from six samples.

It returns dictionaries containing validation results, nucleotide mismatches, sample-level statistics and statistical comparisons. Printed outputs include mismatch percentages, substitution frequencies, the three most frequently mismatched positions and two-sided Welch's t-test results.

The analysis found that 60.3% of valid reads from treated samples contained mismatches, compared with 8.3% in controls, demonstrating higher mismatch frequencies following genotoxic treatment.

Code Design

The program separates validation, mismatch detection and dataset analysis into individual functions (validate_read, find_mutations and analyse_reads). This allows each operation to be tested independently, rather than combining everything into one function.

Invalid reads remain in the analysed dataset, with their errors recorded and an empty mutation list. This preserves information about data quality while preventing invalid sequences from affecting mismatch calculations. Alternatively, invalid reads could have been removed entirely, but this would lose useful information.

The summarise_samples function uses nested dictionaries to organise statistics by sample. This supports datasets containing different numbers of samples and groups without requiring fixed sample names. The compare_positions function uses sorting to select the most frequent positions, prioritising earlier positions when counts are tied.

Testing

Three important tests were performed:

Read validation: Lowercase sequences, invalid characters and incorrect lengths were tested to verify normalisation and error reporting.

Read analysis: Mixed valid and invalid reads were tested to confirm correct mutation detection, preservation of input order and unchanged original data.

Position comparison: A dataset containing tied mismatch counts and a sample with no valid reads verified position ranking, percentage calculations and appropriate sample exclusion.

All tests passed.
