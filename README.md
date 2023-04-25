# Human adenovirus typing database
Typing of human adenovirus (HAdV) is based on [nucleotide identity](https://journals.asm.org/doi/10.1128/JVI.00354-11) in the penton, hexon and fiber (PHF) regions. There are 113 human adenovirus types. 52 of them are non-recombinant, including 51 [original types](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7171713/) and [HAdV-G52](https://journals.asm.org/doi/full/10.1128/JVI.02650-06).
61 of them are recombinant, of which the references for HAdV-D112, HAdV-C108, and HAdV-D90 are currently unavailable.
This database includes the penton, hexon, and fiber sequences for all 52 non-recombinant human adenovirus types, as well as any unique penton, hexon, and fiber sequences for human adenovirus 53 and above.
Specifically, the PHF databases include:

P: C1, C2, B3, E4, C5, C6, B7, D8, D9, D10, B11, A12, D13, B14, D15, B16, D17, A18, D19, D20, B21, D22, D23, D24, D25, D26, D27, D28, D29, D30, A31, D32, D33, B34, B35, D36, D37, D38, D39, F40, F41, D42, D43, D44, D45, D46, D47, D48, D49, B50, D51, G52, D53, D54, D56, D58, D60, D62, D64, D65, B66, D67, D70, D72, D75, D83, D88, C89, D92, D95, D98, D100, D101, D102, D103, D105

H: C1, C2, B3, E4, C5, C6, B7, D8, D9, D10, B11, A12, D13, B14, D15, B16, D17, A18, D19, D20, B21, D22, D23, D24, D25, D26, D27, D28, D29, D30, A31, D32, D33, B34, B35, D36, D37, D38, D39, F40, F41, D42, D43, D44, D45, D46, D47, D48, D49, B50, D51, G52, D54, C57, D58, D59, A61, D62, D70, D74, D107, D110

F: C1, C2, B3, E4, C5, C6, B7, D8, D9, D10, B11, A12, D13, B14, D15, B16, D17, A18, D19, D20, B21, D22, D23, D24, D25, D26, D27, D28, D29, D30, A31, D32, D33, B34, B35, D36, D37, D38, D39, F40, F41, D42, D43, D44, D45, D46, D47, D48, D49, B50, D51, G52, D56, D60, D62, D67, D69, D71, D72, D84


References were obtained from [ICTV](https://ictv.global/report/chapter/adenoviridae/adenoviridae/mastadenovirus) and [HAdV Working Group](http://hadvwg.gmu.edu/) with two substitutions:
- AC_000008 replaces M73260 for HAdV-C5 (AC_000008 and M73260 are identical in the PHF regions, but AC_000008 is the GenBank RefSeq and has annotaions for PHF)
- HQ910407 replaces AF108105 for HAdV-D17 (HQ910407 has annotation for hexon and is the updated sequence for HAdV-D17 according to [Seto et al.](https://journals.asm.org/doi/10.1128/JVI.06051-11))

## Note
- The sequence headers in the fasta files come in the format of >reference-accession_type_region, e.g. >AF534906_HAdV-C1_hexon.
- HAdV F40, F41, and G52 have two fiber sequences, long fiber and short fiber. It is their *long fiber* sequences that are used in this database.
- The PHF sequences are HAdV-C108 (P1H2F2) and HAdV-D90 (P33H27F67) are available so they can be typed, but not for HAdV-D112 (P112H112F67) because its reference penton and hexon sequences are unavailable.

## Usage
This is only a BLAST database and the full typing workflow is not automated. However, only some simple bash scripting is needed to use this database. For example, with BLAST and the PHF databases installed, you can use the following command in a CLI to find the penton sequence (similarly for hexon and fiber sequences) that shares the highest nucleotide identity with the input sequence:

	blastn -query input.fasta -db blastn_db_penton/hadv_types_ref_penton.fa -outfmt 6 -max_target_seqs 1 -evalue 1e-5

You can then use additional bash scripting to parse and chain BLAST outputs together to your preference.

## Contact
If you have any feedback please raise an issue on GitHub or email aseree@uw.edu.
