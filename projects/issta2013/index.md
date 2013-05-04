---
layout: project
title: "GenProg-FL"
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
   Many techniques on automated fault localization (AFL) have been introduced to assist developers in debugging. Prior studies evaluate the localization technique from the viewpoint of developers: measuring how many benefits that developers can obtain from the localization technique used when debugging. However, these evaluation approaches are not always suitable, because it is difficult to quantify precisely the benefits due to the complex debugging behaviors of developers. In addition, recent user studies have presented that developers working with AFL do not correct the defects more efficiently than ones working with only traditional debugging techniques such as breakpoints, even when the effectiveness of AFL is artificially improved.

   In this paper we attempt to propose a new research direction of developing AFL techniques from the viewpoint of fully automated debugging including the program repair of automation, for which the activity of AFL is necessary.  We also introduce the NCP scores as the evaluation measurement to assess and compare various techniques from this perspective. Our experiment on 14 popular AFL techniques with 4 subject programs shipping with real-life field failures presents the evidence that these AFL techniques performing well in prior studies do not have better localization effectiveness according to NCP scores. Based on experimental results, we suggest that Jaccard should always be used with high priority before some more effective AFL techniques specially proposed for automated program repair occur in the future.

<h3><a  name="2">  GenProg-FL </a></h3>
   To demonstrate the feasibility of our evaluation approach, we have implemented the framework by building GenProg-FL, a tool that enables scalability to repair automatically C programs. GenProg-FL is the modification version of [GenProg](http://dijkstra.cs.virginia.edu/genprog/). GenProg has the ability of fixing bugs in deployed, legacy C programs without formal specifications. With the hypothesis that some missed important functionalities may occur in another position in the same program, GenProg attempts to automatically repair defective program with evolutionary computation: mutation and crossover (i.e., repair rules).

   GenProg does not provide the interface for accepting the localization information on the fault, but rather track down the possible faulty statements through simple statistical approach, although GenProg has successfully fixed many bugs existing among some off-the-shelf programs. Hence, we modified the GenProg by adding the interface for accepting the formatted localization information from various AFL techniques. Recall that the formatted localization information should be a suspiciousness list. GenProg-FL attempts to generate one concrete patch by modifying some statements using randomized algorithm (i.e., genetic programming); To what extent a statement should be selected for modification relies on the corresponding probability. In fact, GenProg-FL and GenProg share the same repair mechanism; the only difference between them is that GenProg-FL allows existing AFL techniques to guide the repair process.

<h3><a name="3">Experiment</a></h3>
   To  identify the effectiveness of various AFL techniques, in our experiment we use GenProg-FL to repair 4 real-life faulty programs shipping with true field failures, under the separate guidance of 14 popular statistical AFL techniques. This experiment also plans to investigate that whether the conclusions drawn under the evaluation measurement of EXAM still hold according to NCP measurement. In addition, the experimental results present some useful advices on selecting some AFL techniques from existing ones to effectively guide the repair process before some more effective AFL techniques, which can have better guidance effectiveness on automated program repair, occur in the future.

<h3><a name="4">Results</a></h3>
   Result data in our experiment show that:
   +these AFL techniques performing well under the evaluation measurement of EXAM do not have good performance from the viewpoint of fully automated program repair;
   +Jaccard performs at least as good as the other 13 investigated techniques, with the effectiveness improvement up to "large" effect size using $A$-test. Hence, although more experiments are needed before strong conclusions can be drawn, we suggest that Jaccard should always be used with high priority to provide fault information for these techniques on automated program repair before some more effective AFL techniques are proposed in the future.

<h3><a name="5">Tools and Data</a></h3>
   We give all the experimental results in our ISSTA paper. For each subject program, we separately run GenProg-FL to fix the bug according to 14 different AFL techniques. We record the repair log and data, resulting in some compression files (i.e., rar files) named with the corresponding subject programs. For one compression file such as php.rar, there are 14 different folders, each of which includes both the repair log (debug and best folders) and statistic data (*-statistic.txt) corresponding to one AFL technique. In addition, the Matlab script (named process.m) used to analyze the result data in our paper is presented in each rar file. You can directly run the process.m on Matlab once the rar file is decompressed. 

  + Repair tool: [GenProg-FL](http://dijkstra.cs.virginia.edu/genprog/)
  + [Automated fault localization tool](http://dijkstra.cs.virginia.edu/genprog/)
  + Results data: [libtiff](http://sourceforge.net/projects/afl/files/libtiff.rar) (including 8 fault versions), [python](http://sourceforge.net/projects/afl/files/python.rar), [php](http://sourceforge.net/projects/afl/files/php.rar), [wireshark](http://sourceforge.net/projects/afl/files/wireshark.rar). Note that the source code of subject programs can be obtained from [here](https://church.cs.virginia.edu/genprog/archive/genprog-105-bugs-tarballs/).
