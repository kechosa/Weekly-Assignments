efetch -db=sequences -id=CP000141.1 -format=fasta>C_hydro.fasta
>This command finds, downloads, and creates a fasta file for the chosen reference genome Carboxydothermus hydrogenoformans Z2901 from the NCBI database. -db specifies the database to search in, for this assignment we want the nucleotide sequence so we search the sequences database. After -id we list the accession number of the target genome in this case it is C.hydrogenoformans. -format is used to specify the file type we would like to save. For this we want a fasta file so that it only contain the genome's nucleotide sequence. 

gdown.pl https://drive.google.com/file/d/1PWWO5wVRRThLBXXEZjyWZHIb9udVcnCS/edit C_ferrir_R1.fastq

gdown.pl https://drive.google.com/file/d/1mZFvpSIctuBihkOlQX9vhrkxng3cRmvK/edit C_ferrir_R2.fastq
>The gdown.pl command is used to obtain the raw Carboxydothermus ferrireducens sequencing reads from google drive and save them as fastq files.

bowtie2-build C_hydro.fasta C_hydro
>bowtie2-build is used to make sure that our reference C. hydrogenoformans genome is able to searched and mapped against the two raw reads to obtain our required information.

fastqc C_ferrir_R1.fastq

fastqc C_ferrir_R2.fastq
>Running the fastqc command will create files to assess the quality of the reads of the sequences. These files can be viewed using WinSCP, or a similar program, to access the created html file on your browser.

cutadapt -q 20,20 -a CTGTCTCTTATACACATCTCCGAGCCCACGAGAC -A CTGTCTCTTATACACATCTGACGCTGCCGACGA -m 50 --max-n 0 -o C_ferrir_R1.cutadapt.fastq -p C_ferrir_R2.cutadapt.fastq C_ferrir_R1.fastq C_ferrir_R2.fastq
>cutadapt is used to perform trimming on the two raw sequences so that only quality data is mapped to the reference seqeuence. -q is used to specify the minimum quality score allowed, for this assignment we chose a score of 20 for both reads. -a and -A search for adaptor sequences to trim in the forward and reverse reads, with -a specifying forward read and -A for reverse read. -m is used to signal the minimum length of reads, here we have used 50, anything less than 50 nucleotides will be trimmed. max-n determines the number of no calls allowed, for this we want all excluded so we set that as 0. -o signals the forward output and is where we specify the names of our new files. -p is used to signal the reverse output and is where we state the files on which we wish to use cutadapt.

bowtie2 -x C_hydro -1 C_ferrir_R1.cutadapt.fastq  -2 C_ferrir_R2.cutadapt.fastq -S C.hydro_C.ferrir.sam
>To map the two raw reads to the reference genome we use the bowtie2 command -x is used to call the reference read. -1 and -2 signal that the raw read files we are mapping against the reference are paired ends. -S is used to specify our output file which will be a .sam file which is a file type used for alignments.

samtools flagstat C.hydro_C.ferrir.sam
>samtools flagstat is used to show the simple stats, such as percentage mapped, of a chosen .sam file.
