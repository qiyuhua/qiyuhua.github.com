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
    miaodian : 'GenProg-FL'
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
 According to Algorithm 2 in our paper, we implemented RSRepair by modifying GenProg, which is written in OCaml language. Specifically, RSRepair uses the same implementation of fault localization and matuation as GenProg in

<h3><a name="3">Experiment</a></h3>
   To  identify the effectiveness of various AFL techniques, in our experiment we use GenProg-FL to repair 4 real-life faulty programs shipping with true field failures, under the separate guidance of 14 popular statistical AFL techniques. This experiment also plans to investigate that whether the conclusions drawn under the evaluation measurement of EXAM still hold according to NCP measurement. In addition, the experimental results present some useful advices on selecting some AFL techniques from existing ones to effectively guide the repair process before some more effective AFL techniques, which can have better guidance effectiveness on automated program repair, occur in the future.

<h3><a name="4">Results</a></h3>
   Result data in our experiment show that:
   +these AFL techniques performing well under the evaluation measurement of EXAM do not have good performance from the viewpoint of fully automated program repair;
   +Jaccard performs at least as good as the other 13 investigated techniques, with the effectiveness improvement up to "large" effect size using $A$-test. Hence, although more experiments are needed before strong conclusions can be drawn, we suggest that Jaccard should always be used with high priority to provide fault information for these techniques on automated program repair before some more effective AFL techniques are proposed in the future.

<h3><a name="5">Tools and Data</a></h3>
   We give all the experimental results in our ISSTA paper. For each subject program, we separately run GenProg-FL to fix the bug according to 14 different AFL techniques. We record the repair log and data, resulting in some compression files (i.e., rar files) named with the corresponding subject programs. For one compression file such as php.rar, there are 14 different folders, each of which includes both the repair log (debug and best folders) and statistic data (*-statistic.txt) corresponding to one AFL technique. In addition, the Matlab script (named process.m) used to analyze the result data in our paper is presented in each rar file. You can directly run the process.m on Matlab once the rar file is decompressed. 

  + Repair tool: [GenProg-FL](http://sourceforge.net/projects/afl/files/GenProg-FL.tar.bz2)
  + Automated fault localization tool
  + Results data: [libtiff](http://sourceforge.net/projects/afl/files/libtiff.rar) (including 8 fault versions), [python](http://sourceforge.net/projects/afl/files/python.rar), [php](http://sourceforge.net/projects/afl/files/php.rar), [wireshark](http://sourceforge.net/projects/afl/files/wireshark.rar). Note that the source code of subject programs can be obtained from [here](https://church.cs.virginia.edu/genprog/archive/genprog-105-bugs-tarballs/).
