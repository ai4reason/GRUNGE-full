# GRUNGE

This is the full GRUNGE benchmark for evaluating large-theory ATPs working
in different formalisms - FOF, TF0, TF1, TH0 and TH1.

The benchmark is based on the HOL4 standard library -
https://github.com/HOL-Theorem-Prover/HOL .

For details see https://arxiv.org/abs/1903.02539 :

Chad E. Brown, Thibault Gauthier, Cezary Kaliszyk, Geoff Sutcliffe,
Josef Urban: GRUNGE: A Grand Unified ATP Challenge. CADE 2019: 123-141

The HOL4 licence applies to all files.

The repository contains also the code for generating the problems and
both the bushy and chainy versions of the problems.

The generated problems are compressed in the Generated directory. They
unpack to over 30 GB.

The hol4totptpfol directory contains the code for generating the
syntactic translations via first-order encodings (Section 4 of the
paper).

The hol4totptpset directory contains the code for generating the
semantic translations via set theory encodings (Section 5 of the
paper).

The work was supported by the ERC grants no. 649043 AI4REASON and
no. 714034 SMART and by the Czech project AI&Reasoning
CZ.02.1.01/0.0/0.0/15 003/0000466 and the European Regional
Development Fund.







