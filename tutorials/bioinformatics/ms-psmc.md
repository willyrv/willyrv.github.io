---
layout: post
title:  "Applying PSMC to simulated data"
date:   2015-07-05 18:38:58
---


Applications of PSMC to MS-simulated data
=========================================

This is a simple tutorial showing how to use PSMC to infer the demographic
history from full DNA sequences. We start by applying PSMC to simulated data.

For simulations we will use the software ms [1]. The code may be
downloaded from [here](https://webshare.uchicago.edu/xythoswfs/webui/_xy-218240_1-t_DunQ7c99).
You can also download a compiled version [here](http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/ms), or type

```
    wget http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/ms
```



You need to verify that the file *ms* has execution permissions. In order to give execution permissions to the file type:

```
  chmod 775 ./ms
```

Let's start from one simple simulation. We will generate the first dataset used in the Supplementary Materials of Li and Durbin paper ( *Heng Li & Richard Durbin, Inference of human population history from individual whole-genome sequences,  Nature 475, 493–496 (28 July 2011) doi:10.1038/nature102312011*).

**1-) Run:**

```
./ms 2 100 -t 30000 -r 6000 30000000 -eN 0.01 0.1 -eN 0.06 1 -eN  0.2 0.5 \
-eN 1 1 -eN 2 2 -p 8  > sim1_results.ms
```

Normally this takes less than a minute and should produce one output file (called “sim1_results.ms”). Now we will use a python script to convert this ms output into the input file of psmc. You can download the script [here](http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/ms2psmcfa.py).

```
  wget http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/ms2psmcfa.py
```

The file must has execution permissions:

```
  chmod 775 ./ms2psmcfa.py
```

**2-) Run:**

```
  ./ms2psmcfa.py ./sim1_results.ms > sim1.psmcfa
```

This creates the file “sim1.psmcfa” wich is the input of psmc. (This step is also fast, less than a minute)

Now we can run the PSMC analysis.
Download a compiled version of the psmc software from [here](http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/psmc) or type:

```
  wget http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/psmc
  chmod 775 ./psmc
```

We run the PSMC with the default parameters.

**3-) Run:**

```
  ./psmc -N25 -t15 -r5 -p 4+25*2+4+6 -o dem_history_sim1.psmc ./sim1.psmcfa
```

This is a little bit long (about 3 hours). You should have a file like [this](http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/result_files/dem_history_sim1.psmc)

```
  wget http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/result_files/dem_history_sim1.psmc
```

Plot the result using the provided perl script:
Once the psmc analysis is finished, you can plot the results by using one of the scripts provided with the psmc. You can download it from [here](https://github.com/lh3/psmc/blob/master/utils/psmc_plot.pl)
or from [here](http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/psmc_plot.pl)

```
  wget http://wrodrigu.perso.math.cnrs.fr/GTPB/tutorial_psmc/psmc_plot.pl
```

**4-) Run:**

```
  ./plot_results.py
````

And you will finally get the inferred demographic history.
