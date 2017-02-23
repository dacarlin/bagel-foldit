# Instructions for designing mutations to BglB using the protein editor Foldit Standalone

**Update 22 Feb 2017**: changed instructions to use [Foldit Standalone](http://fold.it/dist/internal/build/).   

## Loading and saving structures

To load your protein:

"Load FASTA/PDB" from the first screen opens a file selection window, select all 5 files:

- `bglb.pdb`
- `pNPG.params`
- `pNPG.conf.pdb`
- `BglB-pNPG.cnstr`
- `BglB-pNPG.puzzle_setup`

and choose "Open" to load the BglB-pNPG model into Foldit Standalone. Within Foldit, `Ctrl-Alt-Shift-A` to load in a structure.

To save a PDB file (XYZ coordinates): `Ctrl-Alt-Shift-S`.

## Recommended view options

+ "Cartoon Thin"
+ "Score/Hydro+CPK"
+ show/hide bonds/voids as needed for context

## Inspect individual residue energies

Mouse over residue so it is highlighted and hit `Tab`.

This info panel gives a breakdown of the various score terms for the selected residue. Importance of score is in order as it appears in the menu

## Viewing operations

+ Zoom to Area of Interest: Mouse over residue of interest so it is highlighted;  hit `Shift-Q`  (no click) I often move around until I see the ligand and then do this

+ BackShading:  `Ctrl-Shift-Click` (on black backdrop) and drag

+ Front Clipping:  `Ctrl-Alt-Click` (on black backdrop) and drag

+ Measuring:  Mouse over atom1 of interest, hit `Ctrl-Alt-Shift-C` (no click), repeat for atom 2 (reports distance), atom 3 (angle), and atom 4 (dihedral)

## Selection operations

+ Select a sphere of residues around a residue that you are hovering over: `Ctrl-Shift-click` on residue and drag outwards

+ See upper left corner of Foldit for number of residues selected

## Using the Lua terminal  

+ From main options, select "Script Terminal"
+ Select specific residue: `selection.Select(i)`, where `i` is the residue index
+ Zoom to specific residue: `ui.CenterViewport(i)`

## How to design mutants in Foldit

+ Click residue and hit mutate (`m`) to see options for new residues
+ Selecting a subset of residues (lower right boxes) can be used to do directed designs
+ Selection will be used in both mutate and shake (i.e. shake now mutates those residues while everything else stays native).
+ **Never** wiggle (`w`) without selecting a sub-selection
+ Sometimes high energies (mutations/conformations) are need to get to the low energy
+ Native amino acid or close to native amino acid is generally better
+ Manually force the interaction you want and then side-chain wiggle (`E`) those residues and the ones around it
+ General order of operations:  `E` → `S` → `E`
+ If score is not dropping faster than 0.05/s you are likely at an energy minimum. This is true **only for** wiggling (`w`/`e`).  If you are shaking (`s`) pay attention to the number of cycles on the upper left corner.  Often the low energy is found after 5-10 cycles (cycles is the number in the parentheses after the timer).

## How to choose mutants

For an individual residue:

+ Total energy less than 0 is good
+ Total energy between 0 and +2 can be OK if clash score (fa_rep) is <1
+ Total energy between +2 and +5 are iffy, but can work if you think the Rosetta picture of the protein is missing an enabling feature
+ Total energy between +5 and +10 are are unlikely. Something will likely have to move for this to work, thus the protein is unlikely to look like your model
+ Energies >+10 are are really unlikely to work… but go for it if you have a good reason

Don't worry about the total protein score too much, as long as it is less than native, or not more than 5 Rosetta Energy Units higher than native.

Focus on the molecular interactions in the neighborhood of the residue you are mutating
