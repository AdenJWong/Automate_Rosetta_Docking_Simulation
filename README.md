# Rosetta Docking Automation Script

This script automates the process of extracting zip files, converting CIF files to PDB format using Open Babel, combining PDB files with predefined PDB files, and running Rosetta docking simulations. The script also handles cleanup of intermediate files and directories.

## Purpose

The purpose of this script is to streamline the workflow for running Rosetta docking simulations. It automates the following steps:
1. Extracts zip files containing CIF files.
2. Converts CIF files to PDB format using Open Babel.
3. Combines the converted PDB files with two predefined PDB files (`a_syn1.pdb` and `a_syn2.pdb`).
4. Runs Rosetta docking simulations on the combined PDB files.
5. Cleans up intermediate files and directories, keeping only the final output.

## Prerequisites

To run this script, you need the following software and files installed and properly configured on your system:

### Software Requirements

1. **Open Babel:** A chemical toolbox designed to speak the many languages of chemical data.
   - Install Open Babel using package managers:
     - On Ubuntu/Debian: `sudo apt-get install openbabel`
     - On macOS: `brew install open-babel`
   - Alternatively, you can compile and install Open Babel locally if you don't have sudo permissions. See the [Open Babel installation guide](https://openbabel.org/wiki/Category:Installation).

2. **Rosetta Software Suite:** A comprehensive software suite for macromolecular modeling.
   - Ensure you have compiled Rosetta and have the `docking_prepack_protocol` executable available.
   - Refer to the [Rosetta installation guide](https://www.rosettacommons.org/software/license-and-download) for detailed instructions.

3. **Zip Utility:** Ensure you have the `unzip` utility installed to extract zip files.
   - On Ubuntu/Debian: `sudo apt-get install unzip`
   - On macOS: `brew install unzip`

### File Requirements

1. **a_syn1.pdb and a_syn2.pdb Files:**
   - These are predefined PDB files required for combining with the converted CIF files.
   - Ensure these files are located in the correct directory specified in the script (e.g., `/global/home/hpc5497/a_syn/a_syn1.pdb` and `/global/home/hpc5497/a_syn/a_syn2.pdb`).

2. **Input Folder with Zip Files:**
   - Prepare an input folder (`zip_files`) containing zip files. Each zip file should contain CIF files that will be converted to PDB format.
   - The script assumes this folder is located at `/global/home/hpc5497/zip_files`.

## Running the Script on Rocky Linux

### Install Prerequisites on Rocky Linux

1. **Enable EPEL Repository:**
   - The EPEL (Extra Packages for Enterprise Linux) repository contains additional packages, including Open Babel.

   ```bash
   sudo dnf install epel-release

2. - Add Open Babel to PATH

   ```bash
   export PATH=$HOME/openbabel/bin:$PATH
   export LD_LIBRARY_PATH=$HOME/openbabel/lib:$LD_LIBRARY_PATH

