#Fragmentation_Replication_Instructions

##1) instal requiered software

    a) visit https://github.com/Hintzelab/MABE/wiki

    b) follow instructions in: Installation and quick start
 
        This will go through the process of installing MABE and all requierments. 
        
        You don't need to compile MABE, but it's not going to hurt, and will make you farmiliar with the process.
 
 
2) download this repository

3) build MABE

    a) navigate to the main level of the downloaded repository (here you should see modules.txt, and the tools and code directories along with some other files and directories)
 
    b) from the command line, run 'sh tools/setup.cmd'

        this will get the correct version of mbuild for your operating system
 
    c) from the command line run './mbuild' (or ./mbuild.exe if on windows)

        this will build MABE with the requiered modules
 
    d) run 'cd work'
 
    e) run 'cp ../runFiles/*' .
 
 
 
4) run experiments
 
    a) from the command line run 'python ../tools/mq.py'

        you should see some output that says that 3 jobs will be run (BlockCatch with Markov Brains and RNN and NBack with RNN)
 
    b) run 'python ../tools/mq.py -l'

        this will run the 3 jobs using random seed 101 for each - this may take a long time!

        the results will be in directories starting with 'C' and then the conditoin number and desciption

        each condition directory will contain the reps run for the condition, and each rep directory will contain the data files.
 
    c) for more on running MABE and using mq see https://github.com/Hintzelab/MABE/wiki 

5) generating Fragmentation Matrix and Data Flow plots

    a) once you have run the conditions you are interested in visualizing, run 'cd ../analyze'

    b) run 'python analyzeSingle.py ../../C0__WRLD_BlockCatch__BRN_Markov__UPD_20000/101/'

        this will run MABE in analyze mode for the given condition and rep number

        note: if you change the conditions or rep numbers you will need to change the path argument

        note: if you run again with a different condition or rep number the current data will be overwritten

    c)to create a Fragmentation Matrix plot:

        run 'python makeFragVisualization.py -fragMap fragMap_75_100 -fileName R_with_inputs_FragmentationMatrix_id_0.py -skipRange .025 .99 -fontSize 4 -saveName FragMatrix.pdf'

        ote: this will save the image FragMatrix.pdf

        note: you can run python makeFragVisualization.py -h to see other options

    d) to create a Data Flow plot:

    when you ran the analysis, a set of files called, flowPlot_0_25_id_0.dot, flowPlot_0_100_id_0.dot, and flowPlot_75_100_id_0.dot were generated

    these file have early (0_25 = first 25%), full (0_100 = full), and late (75_100 = last 25%) life data flow data.

    these files are formatted to work with graphviz, the fastest way to view them is with an online viewer such as: dreampuf.github.io/GraphvizOnline

    navigate to the viewer of your choice and copy the contents to the file you want to view into the viewer (the 'cat' command is useful to see the file contents)
