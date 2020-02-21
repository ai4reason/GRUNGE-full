
Here are the instructions for reproducing the GRUNGE dataset.

## Install HOL

- Install Poly/ML.
- Extract the archive HOL-GRUNGE.tar.gz.
- Follow the instruction in the HOL-GRUNGE/INSTALL file to install HOL.
- Launch an interactive session by calling hol or (rlwrap hol for easier input).

## S-Expression 
To produce the S-expressions using in the second translation run:

  load "hhExportSexpr"; open hhExportSexpr;
  load "tttUnfold"; open tttUnfold; 
  load_sigobj ();
  val thyl = ancestry "scratch";
  hhExportSexpr.sexport_export thyl;

## Bushy and Chainy problems

To produce the bushy and chainy problems in FOF:

  load "hhExportFof"; open hhExportFof;
  load "tttUnfold"; tttUnfold.load_sigobj ();
  val thyl = ancestry (current_theory ());
  val bushydir = HOLDIR ^ "/src/holyhammer/fof_bushy";
  fof_export_bushy bushydir thyl;
  val chainydir = HOLDIR ^ "/src/holyhammer/fof_chainy";
  fof_export_chainy chainydir thyl;

Similar functions are available for the four other formats and the pseudo-code
for the export is available at the end of the files 
hhExportTh1.sml hhExportTh0.sml hhExportTf0.sml hhExportTf1.sml

To create datasets for a new version (available from March 2020) of HOL,
download HOL from the main repository and repeat the previous steps.
