---
layout: project
title: "rsrepair"
miaodians:
  #- 
  #  url : '/footmark/index.html'
  #  title : '#'
  - 
    miaodian : 'Introduction'
    url : '#1'
  -
    miaodian : 'RSRepair'
    url : '#2'
  -
    miaodian : 'Experiment'
    url : '#3'
  -
    miaodian : 'Results'
    url : '#4'
  -
    miaodian : 'Tools and Data'
    url : '#5'
---
{% include JB/setup %}

<h3><a  name="1"> Introduction </a></h3>
   Automated program repair received considerable recent attention, and many techniques on this research area have been proposed. Among these techniques, two genetic-programming-based techniques, GenProg and Par, have shown the promising results. In particular, GenProg has been used as the baseline technique to check the repair effectiveness of new techniques in much literature. Although GenProg and Par have shown their strong ability of fixing real-life bugs in nontrivial programs, to what extent GenProg and Par can benefit from genetic programming, used by them to guide the patch search process, is still unknown.

   To address the question, in this paper we present a new automated repair technique using random search, which is commonly considered much simpler than genetic programming, and implement a prototype tool called RSRepair. Experiment on 7 programs with 24 versions shipping with real-life bugs suggests that RSRepair, in most cases (23/24), outperforms GenProg in terms of both repair effectiveness (requiring fewer patch trials) and efficiency (requiring fewer test case executions), justifying the stronger strength of random search over genetic programming. According to experimental results, we suggest that every proposed technique using optimisation algorithm should check its effectiveness by comparing it with random search.

<h3><a  name="2">  RSRepair </a></h3>
   According to Algorithm 2 in our paper, we implemented RSRepair by modifying GenProg, which is written in OCaml language. Specifically, RSRepair implements the functions of fault localiztion and matuation in the way like GenProg.

   In fact, RSRepair produces candidate patches in the same way of generating randomly patches in the first generation of GenProg but without fitness guidance and crossover in the subsequent generations.  For the process of patch validation, RSRepair validates candidate patches in the way described in Algorithm 2 in our paper.

<h3><a name="3">Experiment</a></h3>
   To check the performance of RSRepair, we compare it with GenProg, a state-of-the-art tool on automated program repair, on 7 subject programs with 24 faulty versions. We selected GenProg for the reason that GenProg is almost the only state-of-the-art automated repair tool which can fix bugs in real-world, large-scale C programs. Our experimental evaluation seeks to address the following Research Questions:


  + RQ1: How well does genetic programming, the optimisation algorithm used by GenProg, perform over random search, used by RSRepair?
  + RQ2: Does GenProg find a valid patch much faster than RSRepair in terms of requiring fewer Number of Test Case Executions (NTCE) within a successful repair process?

<h3><a name="4">Results</a></h3>
   Result data in our experiment show that:
   +In our experiment, for most programs (23/24), random search used by RSRepair performs better than genetic programming used by GenProg, regardless of whether genetic programming really starts to work or not.
   +GenProg does not find a valid patch faster than RSRepair. Oppositely, in most cases, GenProg requires much more NTCE to repair faulty programs, leading to the lower repair efficiency than RSRepair.

<h3><a name="5">Tools and Data</a></h3>
   We give all the experimental results in our ICSE paper. For each subject program, we separately run RSRepair and GenProg to fix the bugs in 7 nontrivial programs with 24 versions. We record the repair log and data, resulting in some compression files (i.e., rar files) named with the corresponding subject programs. For one compression file such as php.rar, there are severval different folders, each of which includes both the repair log (debug and best folders) and statistic data (*-statistic.txt) corresponding to each program version. In addition, we also present the Matlab script (named process.m) used to analyze the result data in our paper. You can directly run the process.m on Matlab once all the rar file is decompressed. 

  + Repair tool: [RSRepair](http://sourceforge.net/projects/rsrepair/files/RSRepair.tar.bz2), [GenProg](http://dijkstra.cs.virginia.edu/genprog/)
  + Matlab script: [process.m](http://sourceforge.net/projects/rsrepair/files/process.m)
  + Results data: [libtiff](http://sourceforge.net/projects/rsrepair/files/libtiff.tar.bz2) (including 15 fault versions), [lighttpd](http://sourceforge.net/projects/rsrepair/files/lighttpd.tar.bz2) (including 4 fault versions), [gmp](http://sourceforge.net/projects/rsrepair/files/gmp.tar.bz2) , [python](http://sourceforge.net/projects/rsrepair/files/python.tar.bz2), [php](http://sourceforge.net/projects/rsrepair/files/php.tar.bz2), [gzip](http://sourceforge.net/projects/rsrepair/files/gzip.tar.bz2), [wireshark](http://sourceforge.net/projects/rsrepair/files/wireshark.tar.bz2). Note that the source code of subject programs can be obtained from [here](https://church.cs.virginia.edu/genprog/archive/genprog-105-bugs-tarballs/).
