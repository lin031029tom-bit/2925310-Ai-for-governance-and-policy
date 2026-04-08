Policy Classifier Lightweight Replication

This repository contains a lightweight replication package for the report:

Replicating an NLP-Based Policy Classification Study: A Critical Assessment of Incentive Classification for Policy Analysis

The replication is based on the public materials released for:

Waskow, M.A. and McCrae, J.P. (2025) Enhancing Policy Analysis with NLP: A Reproducible Approach to Incentive Classification.

Purpose

This package is designed to meet the coursework requirement that all replication code can be run with a single execution on another machine. It provides a simplified offline baseline rather than a full reproduction of the paper’s final transformer-embedding pipeline.

Included files

The repository includes the following files required for one-command execution:

run_replication.sh
replication_light.py
19Jan25_firstdatarev.json
27Jan25_query_checked.json
requirements.txt

It may also include generated output files:

merged_dataset.csv
replication_results.json
replication_summary.txt
Install dependencies

Install the required Python packages with:

pip install -r requirements.txt
Run the replication

Execute the full replication workflow with:

bash run_replication.sh
What the script does

The replication script:

loads the two labelled JSON input files;
extracts sentence-label pairs;
removes empty and unsure labels;
applies near-duplicate removal using a rapidfuzz-style threshold;
reconstructs the merged dataset;
runs a lightweight TF-IDF + class-balanced LinearSVC baseline across ten stratified 60/20/20 splits;
writes output files to the working directory.
Expected outputs

Running the script generates:

merged_dataset.csv
replication_results.json
replication_summary.txt
Notes
This is a partial replication of the public workflow.
It is not an exact reproduction of the paper’s final transformer + SVM pipeline.
The script is intentionally lightweight so that it can run locally in one command without downloading large model weights.
The reconstructed dataset matches the published total row count of 1,419, but the incentive count differs slightly from the paper’s reported figure.
Replication summary

Expected headline results from the lightweight baseline:

Rows after deduplication: 1,419
Binary counts: Non-Incentive = 1,150; Incentive = 269
Binary weighted F1: 86.7 ± 0.9
Binary macro F1: 78.1 ± 1.8
Multiclass weighted F1: 88.0 ± 3.4
Multiclass macro F1: 82.1 ± 5.7
