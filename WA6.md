wget https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/Unk_therm.faa
>The wget command finds and downloads the file containing the list of proteins from our unknown thermophile.

makeblastdb -in Unk_therm.faa -dbtype prot -title Unk_protein
>makeblastdb is used to create a BLAST database. -in specifies that what file to use to make our blastable database. -dbtype allows to specify what type of database we'd like to make, for this assignment we need a protein database, which is signified by prot. -title is where the name of the output files is specified.

wget https://github.com/stechtmann/BL4300-5300/raw/master/data/Weekly_Assignment_data/HSP_prot.fasta
>The second wget command is used to download our query of heat shock proteins that we will blast against our unknown's protein sequences to find possible homologous heat shock proteins in the unknown.

blastp -db Unk_therm.faa -query HSP_prot.fasta -out HSP_BLAST.txt -outfmt 7
>blastp specifies that we want to run a protein BLAST. -db specifies which database to run and -query specifies what we'd like to compare our unknown's proteins against. -out specifies the name of the output file and -outfmt specifies which BLAST format we'd for our BLAST output.

less HSP_BLAST.txt
>The less command is used to search the output BLAST file to find the possible heat shock proteins for our unknown organism.
