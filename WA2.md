### Determining the number of protein sequences

wc -l coffee_chloroplast.fasta

output=170
>wc -l tells us the total number of lines in the file. With an output of 170 that means there are 85 protein sequences as each protein will contain two lines; one for the name and one for the sequence.

### Creating a file of protein sequences’ names

head coffee_chloroplast.fasta
>Using the head command will determine what all the lines containing the protein sequence names have in common and for the chloroplast from the coffee genome it was found that all the lines with the names contain “NC_008535”

grep “NC_008535” coffee_chloroplast.fasta | sort>coffee_chloroplast_proteins.txt
>Using the command grep "NC_008535" coffee_chloroplast.fasta all the lines from the file containing NC_008535 will be pulled from file, which in this case is all the names of proteins contained in the coffee chloroplast. This command was piped with the sort command to sort all the names alphabetically. Then using the greater than sign all the sorted protein names were moved into a new file called coffee_chloroplast_proteins.txt.

wc -l coffee_chloroplast_proteins.txt

output=85
>wc -l was run on the file to double check that all the protein names did transfer to the new file.

### There are 22 photosystem proteins 

This was determined using the following command:

grep “photosystem” coffee_chloroplast_proteins.txt | wc -l

output = 22
>Using grep “photosystem” will find all the lines containing the word photosystem by piping this command with wc -l, which gives the number of lines, it was found that there are 22 lines containing the word photosystem, meaning the coffee chloroplast chromosome has 22 photosystem subunit proteins.

### ATP synthase CF1 beta subunit protein

sed -n ‘/ATP synthase CF1 beta subunit/,+1p’ coffee_chloroplast.fasta>ATP_synthase_CF1_beta_subunit.fasta
>sed -n will find and pull the line containing ATP synthase CF1 beta subunit from the file coffee_chloroplast.fasta. By adding ,+1p the line directly following the specified phrase, which is the protein sequence, will also be pulled. The addition of the >ATP_synthase_CF1_beta_subunit.fasta creates a new file containing just the protein name and sequence for ATP synthase CF1 beta subunit.
