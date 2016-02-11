# siphonophore16s

This exercise is an introduction to:

- git and github
- running a raxml analysis
- using Brown's [Oscar Cluster](https://web1.ccv.brown.edu/doc/getting-started.html)


## Steps

Open the terminal on your computer, and log into Oscar with:

    ssh username@ssh.ccv.brown.edu

where `username` is your oscar username.

Then cd into scratch and clone this repository and move to the `run` folder:

    cd ~/scratch
    git clone 
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

Now you will pull the files to your laptop for closer inspection. In the terminal on your laptop (not with ssh to Oscar!):

	cd ~
	mkdir repos # a folder for your git repositories
	cd repos
    git clone 
    cd siphonophore16s/run
    cat RAxML_bipartitions.boot100

This will show the tree in newick format. 

Copy and paste it into FigTree.

