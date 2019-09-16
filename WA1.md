### Piped Command 1

Input: sort WA1.fasta | grep “globin”

Output:

alpha_globin_dog P60529 Canis lupus familiaris (dog)

alpha_globin_horse P01958 Equus caballus

alpha_globin_kangaroo P01975 Macropus giganteus (eastern gray kangaroo)

beta_globin_dog XP_537902 Canis lupus familiaris (dog)

beta_globin_kangaroo P02106 Macropus giganteus (eastern gray kangaroo)

beta_globin_rabbit NP_001075729 Oryctolagus cuniculus (rabbit)

globin_insect P02229 Chironomus thummi thummi (midge)

globin_lamprey 690951A Lampetra fluviatilis (European river lamprey)

globin_sealamprey P02208 Petromyzon marinus (sea lamprey)

globin_soybean 711674A Glycine max (soybean)

myoglobin_gray_seal P68081 Halichoerus grypus

myoglobin_harbor_porpoise P68278 Phocoena phocoena

myoglobin_kangaroo P02194 Macropus rufus (red kangaroo)

### Piped Command 2
Input: head -6 WA1.fasta | wc -c

Output: 
616

### Piped Command 3
Input: head -6 WA1.fasta | tail -8 > myoglobinandglobin.fasta

Output: New file named myglobinandglobin.fasta with the lines

myoglobin_kangaroo P02194 Macropus rufus (red kangaroo)
MGLSDGEWQLVLNIWGKVETDEGGHGKDVLIRLFKGHPETLEKFDKFKHLKSEDEMKASEDLKKHGITVLTALGNILKKKGHHEAELKPLAQSHATKHKIPVQFLEFISDAIIQVIQSKHAGNFGADAQAAMKKALELFRHDMAAKYKEFGFQG

myoglobin_harbor_porpoise P68278 Phocoena phocoena 
MGLSEGEWQLVLNVWGKVEADLAGHGQDVLIRLFKGHPETLEKFDKFKHLKTEAEMKASEDLKKHGNTVLTALGGILKKKGHHDAELKPLAQSHATKHKIPIKYLEFISEAIIHVLHSRHPAEFGADAQGAMNKALELFRKDIATKYKELGFHG

myoglobin_gray_seal P68081 Halichoerus grypus
MGLSDGEWHLVLNVWGKVETDLAGHGQEVLIRLFKSHPETLEKFDKFKHLKSEDDMRRSEDLRKHGNTVLTALGGILKKKGHHEAELKPLAQSHATKHKIPIKYLEFISEAIIHVLHSKHPAEFGADAQAAMKKALELFRNDIAAKYKELGFHG

globin_lamprey 690951A Lampetra fluviatilis (European river lamprey)
PIVDSGSPAVLSAAEKTKIRSAWAPVYSNYETSGVDILVKFFTSTPAAQEFFPKFKGMTSADELKKSADVRWHAERIINAVNDAVASMDDTEKMSMKDLSGKHAKSFQVDPQYFKVLAVIADTVAAGDAGFEKLSMCIILMLRSAY

globin_sealamprey P02208 Petromyzon marinus (sea lamprey)
MPIVDTGSVAPLSAAEKTKIRSAWAPVYSTYETSGVDILVKFFTSTPAAQEFFPKFKGLTTADQLKKSADVRWHAERIINAVNDAVASMDDTEKMSMKLRDLSGKHAKSFQVDPQYFKVLAAVIADTVAAGDAGFEKLMSMICILLRSAY

globin_insect P02229 Chironomus thummi thummi (midge)
MKFLILALCFAAASALSADQISTVQASFDKVKGDPVGILYAVFKADPSIMAKFTQFAGKDLESIKGTAPFEIHANRIVGFFSKIIGELPNIEADVNTFVASHKPRGVTHDQLNNFRAGFVSYMKAHTDFAGAEAAWGATLDTFFGMIFSKM

globin_soybean 711674A Glycine max (soybean)
VAFTEKQDALVSSSFEAFKANIPQYSVVFYTSILEKAPAAKDLFSFLANPTDGVNPKLTGHAEKLFALVRDSAGQLKASGTVVADAALGSVHAQKAVTNPEFVVKEALLKTIKAAVGDKWSDELSRAWEVAYDELAAAIKAK
