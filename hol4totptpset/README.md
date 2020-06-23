This repo contains code to translate from an S-expression version
of the HOL4 library into three tptp formats: TH0, TF0 and FOF.
Before giving a brief description of how to use it, here are
two quotes intended to alienate authoritarians:

*Not the violent conflict between parts of the truth, but the quiet
suppression of half of it, is the formidable evil; there is always
hope when people are forced to listen to both sides; it is when they
attend to only one that errors harden into prejudices, and truth
itself ceases to have the effect of truth, by being exaggerated into
falsehood. - John Stuart Mill*

*Only facts and reason can shed light on these biases, but when it
comes to diversity and inclusion, Google's left bias has created a
politically correct monoculture that maintains its hold by shaming
dissenters into silence. This silence removes any checks against
encroaching extremist and authoritarian policies.  - James Damore*

# S-expressions of HOL4 Library

The directory casc_sexpr_hol4 contains the HOL4 library in S-expression format.
In that directory, the file theories contains a list of the names of the theories in order.
For each theory name there is a file by that name with S-expressions corresponding to the
items in the theory. There may also be a .dep file containing known dependencies for
generating "bushy" files. In some cases the dependencies are broken and no bushy file
will be generated. The dependencies are "intact" if the word "intact" occurs.

For example, the second theory is named "bool". There are files "bool" and "bool.dep".
In the file "bool" there is the conjecture:

    (conjecture "thm_2Ebool_2ETRUTH" "c_2Ebool_2ET")

In the file "bool.dep" there are the lines:

    "thm_2Ebool_2ETRUTH"
    conjecture
    intact
    "thm_2Ebool_2ET__DEF"

This means a bushy problem should be created for the conjecture "thm_2Ebool_2ETRUTH"
with the only dependency being "thm_2Ebool_2ET__DEF".

# Axiom files

There are three axiom files before the generation process:

HL4001^2.ax : basic include file for TH0
HL4001_2.ax : basic include file for TF0
HL4001+2.ax : basic include file for FOF

During the generation of chainy files a new axiom file will
be created for each theory and put into the Axioms subdirectory.
These new axiom files will be include previous theories
back to the HL4001 files recursively.

# Problem files

The problem files are generated into the following subdirectories:

    bushy_th0
    bushy_tf0
    bushy_fof
    chainy_th0
    chainy_tf0
    chainy_fof

Each chainy problem will include the axiom file for the previous
theory to the theory in which the problem occurs.  For example, chainy
problems in bool will include min^2.ax (for TH0).  Bushy problems will
only include the appropriate HL4001 axiom file.

# Generating the problems.

To generate the problems, start sbcl. You may need to use
--dynamic-space-size with a high number (like 100000000) since the
translation requires a lot of memory.

Then load the main code:

    (load "hol4totptpset.lisp")

Then call the following functions (or only the ones corresponding to
the problems you want to generate):

    (gen-bushy-th0)
    (gen-bushy-tf0)
    (gen-bushy-fof)
    (gen-chainy-th0)
    (gen-chainy-tf0)
    (gen-chainy-fof)

Each of these functions first create one large file in the tmp
subdirectory named hol4fof, hol4tf0 or hol4th0 giving the entire
library in the appropriate format. It then uses this file
to create the bushy or chainy problem/axiom files.
