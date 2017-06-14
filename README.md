## Foldit model of BglB for the Bagel project

This repository contains a macromolecular model of BglB that is used for design efforts in the Siegel group's Bagel project. 

**Note:** As of June 2017, there are two copies of Foldit floating around, and they use different constraint file formats. **Foldit Standalone**, the current version of Foldit, uses the constraint file `BglB-pNPG.cnstr`. The older version of Foldit uses the `pNPG.enzdes.cst` file. 

The files in this repo are: 

+ `pNPG.params`, Rosetta params file
+ `pNPG.conf.pdb`, low-energy conformers of the pNPG molecule
+ `pNPG.enzdes.cst`, RosettaMatch-style constraints (for old versions of Foldit)
+ `BglB-pNPG.cnstr`, harmonic Rosetta constraints (for Foldit Standalone)
+ `bglb.pdb`, XYZ coordinates of BglB-pNPG complex 

## Instructions for using Foldit for enzyme design

Use the [instructions for using the protein editor Foldit Standalone](foldit_instructions.md) for designing your point mutations
