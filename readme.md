# siphonophore16s

This exercise is an introduction to:

- git and github
- running a raxml analysis
- using Brown's [Oscar Cluster](https://web1.ccv.brown.edu/doc/getting-started.html)


## Steps

### Forking the repository on github

Browse to the GitHub repository for this exercise. If you are reading this at GitHub, you are already [there](https://github.com/Phylogenetics-Brown-BIOL1425/siphonophore16s).

Click the "Fork" button on the top right of the page. This creates your own independent copy of the repository to work with, so we can all make changes without affecting other peoples' analyses. It also takes you to the web page for the new repository. The url will be something like:

    https://github.com/github_username/siphonophore16s

where `github_username` is your github username.

### Running the analyses on oscar

Open the terminal on your computer, and log into Oscar with:

    ssh oscar_username@ssh.ccv.brown.edu

where `oscar_username` is your oscar username.

Then cd into scratch and clone this repository and move to the `run` folder:

    cd ~/scratch
    git clone https://github.com/github_username/siphonophore16s.git # Substitute github_username with your GitHub username
    cd siphonophore16s/run

And [launch](https://web1.ccv.brown.edu/doc/batch-jobs.html) the run:

    myq
    sbatch mpi_raxml.sh
    myq

The `myq` program checks the status of your job. Execute it as many (or as few) times as you like to see if your analysis is running. Logging out won't stop your job.

When the job is done, add the output files to the repository and push them back to GitHub:

    git add -A .
    git commit -am "added result files from oscar"
    git push

Your results are now up at github. take a look in your `siphonophore16s/run/` folder on GitHub.


### Inspecting the results on your laptop

Now you will pull the files to your laptop for closer inspection. In the terminal on your laptop (not with ssh to Oscar!):

	cd ~
	mkdir repos # a folder for your git repositories
	cd repos
    git clone https://github.com/github_username/siphonophore16s.git # Substitute github_username with your GitHub username
    cd siphonophore16s/run
    cat RAxML_bipartitions.boot100

This will show the tree in newick format. 

Copy and paste it into FigTree. Click the edge that separates Rhizophysa_eysenhardti_60544963, Rhizophysa_filiformis_60544940, and Physalia_physalis_60544938 from the other taxa and click the "Reroot" button at the top of the window. Then, to see bootstrap values, click "Node Labels" on the left side of the page and in the "Display" drop down select "label".

In the FigTree file menu, select "Export PDF..." and save the pdf in the `siphonophore16s/run` folder of your repository as `16s.pdf`.

Now, head back to the command line and add the pdf to the repository:

    git add 16s.pdf
    git commit -am "added pdf of tree"
    git push

The files in the `run directory` include:

- `mpi_raxml.sh` the code that ran your analysis
- `siph16s.phy` the original data file
- `MyMPIJob-11991390.out` the log file that has the program output for the analysis
- `RAxML_bestTree.boot100` the most likely tree
- `RAxML_bipartitions.boot100` the best tree, with bootstrap bipartition frequencies stored as *node* values (this is a bad way to store support, but included with raxml for compatibility with programs that expect bad behavior)



Open `~/repos/siphonophore16s/readme.md` in your text editor, and answer the following questions (just add your answer on a lone below the question):

#### Which clade has the longest branches?
the clade containing the species Vogtia pentacantha, Vogtia glabra and Hippopodius hippopus
#### How strong is the bootstrap support for the placement of Sphaeronectes? Where is it placed?
1) 70
2)it is placed as sister group of a clade containing Muggiaea, Sulcoleolaria, Lensia, Abylopsis, Diphyes and Chelophyes.
#### Bonus: What are the various placements of Clausophyid_sp (hint: you'll need to look in `RAxML_bootstrap.boot100`)
As a sister taxa of the clade Nectoadamas + Nectropyramis, and as sister taxa of Chunyphies multidentata


Once you have saved your answers, commit them with:

    git commit -am "answered questions"
    git push


### Submit your exercise with a pull request

You will submit your repository back to me with a pull request. This is a bundle that describes all the changes you made to your repository. Go to your repository page at GitHub:

    https://github.com/github_username/siphonophore16s

where `github_username` is your github username.

Click the green button that says "New pull request" and then, on the new page that comes up, "Create pull request".

## Aditional resources

The readme.md file is written in a language called [markdown](https://daringfireball.net/projects/markdown/syntax), which looks good as plain text and is automatically formatted for web view on GitHub. An intro to markdown gor GitHub is [here](https://guides.github.com/features/mastering-markdown/).
