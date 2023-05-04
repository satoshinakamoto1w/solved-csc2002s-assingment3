Download Link: https://assignmentchef.com/product/solved-csc2002s-assingment3
<br>
<strong> </strong>

<strong><em>Parallel Programming with the Java Fork/Join framework: Photosynthesis </em></strong>




There is a branch of Botany that is concerned with simulating vegetation patterns using computerized models. This has implications for anticipating the effect that climate change will have on vegetation. These models scale in computational complexity with the size of the input terrain, which in some cases can span entire continents. They are therefore prime candidates for acceleration using parallel programming.




One of the most important factors affecting a tree’s growth is its exposure to sunlight. In this assignment you will efficiently calculate the average sunlight received by trees in a forest (and also record the sunlight exposure of individual trees).




For the purposes of this assignment the landscape is represented by a regular matrix of floating point values. Each value represents the average hours of sunlight per day falling on a 1m x 1m area of the terrain. Not all areas receive the same amount of sunlight because of folds in the landscape (see below).







<em>Figure 1: Average sun exposure during March for a 3km x 3km section of terrain in California. North facing slopes receive less sunlight (and are represented by a darker red in the colour map). South facing slopes tend to receive more sunlight (a bright red or orange in the colour map). </em>




Tree canopies are represented (rather unrealistically) as a square coverage area on the terrain. For the forest you will be provided with the top left (x, y) terrain coordinate of a tree’s canopy indexed from (0,0) and the extent in meters (e).




Your task is to calculate both the total sunlight exposure for each tree canopy (the sum of the sunlight values within its canopy area) and the mean sunlight exposure for all trees.




The file input format is as follows:

&lt;terrain x size – INT&gt; &lt;terrain y size – INT&gt;

&lt;avg. hours sunlight at (0,0) – FLOAT&gt; &lt;avg. hours sunlight at (0, 1) – FLOAT&gt; … &lt;avg.

hours sunlight at (xsize-1, ysize-1) – FLOAT&gt;

&lt;number of trees – INT&gt;

&lt;x corner of tree 0 – INT&gt; &lt;y corner of tree 0 – INT&gt; &lt;canopy extent of tree 0 – INT&gt;

…

&lt;x corner of tree (numtrees-1) – INT&gt; &lt;y corner of tree (numtrees-1) – INT&gt; &lt;canopy extent of tree (numtrees-1) – INT&gt;




For example, a very small 5m x 5m section of terrain, with 2 trees would be encoded in the input file as:

5 5

4.5 5.5 4 3.5 4 4.5 5 4.5 4 4 5 5 5.5 4.5 5 4 4.5 5 5 4 4 4 4.5 4 3.5

2

<ul>

 <li>1 3</li>

 <li>3 4</li>

</ul>




Visually this corresponds to:













Note that some trees may extend beyond the edge of the terrain (as is the case above for the light green tree) and these parts of the canopy should be ignored. Trees may also overlap, but for the purposes of this simulation they do not occlude each other.




The file output format is as follows:

&lt;avg. sunlight per tree – FLOAT&gt;

&lt;number of trees – INT&gt;

&lt;total sunlight tree 0 – FLOAT&gt;

…

&lt;total sunlight tree (numtrees-1) – FLOAT&gt;




For the example above this would mean an output of:

34.5

2

43

26
















In this assignment you will attempt to parallelize the problem in order to speed it up.  You will be required to:




<ul>

 <li>Use the Java Fork/Join framework to parallelize the sunlight exposure calculations using a divide-and-conquer algorithm.</li>

</ul>




<ul>

 <li>Evaluate your program experimentally:</li>

</ul>




<ul>

 <li>Using high-precision timing to evaluate the run times of your serial and your parallel method, across a range of input sizes, and</li>

</ul>




<ul>

 <li>Experimenting with different parameters to establish the limits at which sequential processing should begin.</li>

</ul>




<ul>

 <li>Write a report that lists and explains your findings.</li>

</ul>




Note that parallel programs need to be both <strong>correct </strong>and <strong>faster </strong>than the serial versions.

Therefore, you need to demonstrate both correctness and speedup for your assignment.







<h1>Assignment details and requirements</h1>

Your program will calculate the sunlight exposure of individual trees in parallel as well as the average sunlight exposure of all trees in the forest.

<h2>1.1 Input     and    Output</h2>




Your program must take the following command-line parameters:

&lt;data file name&gt; &lt;output file name&gt;

The format of these files must follow the specification provided above.




We will provide you with a sample input file (on Vula), though you may also create your own using random data.

<h2>1.2      Benchmarking</h2>

You must time the execution of your parallel sorts across a range of data <strong>sizes </strong>and <strong>number of threads </strong>(sequential cutoffs) and report the speedup relative to a serial implementation. The code should be tested on at least <strong>two different machine architectures </strong>(at least one of which must be a multi-CPU/multi-core machine).

Timing should be done at least 5 times. Use the System.currentTimeMillis method to do the measurements. Timing must be restricted to the sunlight exposure code and must exclude the time to read in the files and other unnecessary operations, as discussed in class. Call System.gc()to minimize the likelihood that the garbage collector will run during your execution (but do not call this within your timing block!).




<h2>1.3      Report</h2>

You must submit an assignment report <strong>in pdf format</strong>. Your clear and <strong>concise </strong>report should contain the following:

<ul>

 <li>An <em>Introduction</em>, comprising a short description of the aim of the project, the parallel algorithms and their expected speedup/performance.</li>

 <li>A <em>Methods </em>section, giving a description of your approach to the solution, with details on the parallelization. This section must explain how you validated your algorithm (showed that it was correct), as well as how you timed your algorithms with different input, how you measured speedup, the machine architectures you tested the code on and interesting problems/difficulties you encountered.</li>

 <li>A <em>Results and Discussion </em>section, demonstrating the effect of data sizes and numbers of threads and different architectures on parallel speedup. This section should <strong>include speedup graphs </strong>and <strong>a discussion</strong>. Graphs should be clear and labelled (title and axes). In the discussion, we expect you to address the following questions:</li>

 <li>Is it worth using parallelization (multithreading) to tackle this problem in Java?</li>

 <li>For what range of data set sizes does your parallel program perform well?</li>

 <li>What is the maximum speedup obtainable with your parallel approach? How close is this speedup to the ideal expected?</li>

 <li>What is an optimal sequential cutoff for this problem? (Note that the optimal sequential cutoff can vary based on dataset size and architecture.)</li>

 <li>What is the optimal number of threads on each architecture?</li>

 <li>A <em>Conclusions </em>(note the plural) section listing the conclusions that you have drawn from this project. What do your results tell you and how significant or reliable are they?</li>

</ul>

Please do NOT ask the lecturer for the recommended numbers of pages for this report. Say what you need to say: no more, no less.

<h2>1.4      Assignment           submission           requirements</h2>

<ul>

 <li>You will need to create and submit a GIT archive (see the instructions on Vula on how to do this).</li>

 <li>Your submission archive must consist of BOTH a technical report and your solution code and a <strong>Makefile</strong> for compilation.</li>

 <li><strong>Label </strong>your assignment archive with your<strong> student number </strong>and the<strong> assignment number e.g. KTTMIC004_CSC2002S_Assignment1. </strong></li>

 <li>Upload the file and<strong> then check that it is uploaded.  </strong>It is your responsibility to check that the uploaded file is correct, as mistakes cannot be corrected after the due date.</li>

 <li>The usual late penalties of 10% a day (or part thereof) apply to this assignment.</li>

</ul>

<strong> </strong>

<strong> </strong>

Due date:

10am on 17<sup>th</sup> September 2018










<ul>

 <li><strong>Late</strong> submissions will be <strong>penalized at 10%</strong> (of the total mark) per day, or part thereof.</li>

 <li>The deadline for marking <strong>queries </strong>on your assignment is<strong> one week after the return </strong></li>

</ul>

<strong>of your mark.</strong> After this time, you may not query your mark.




<h2>1.5      Extensions to        the     assignment</h2>

If you finish your assignment with time to spare, you can attempt one of the following for extra credit:

<ul>

 <li>Compare the performance of the Fork/Join library with standard threads.</li>

 <li>Replace the square canopy with a circular canopy and measure the impact that this has on performance.</li>

 <li>Not all trees absorb sunlight with the same efficiency. Add a per tree weighting factor for the sunlight exposure. Again, see what impact this has on speedup.</li>

</ul>




<h2>1.6      Assignment           marking</h2>

Your mark will be based primarily on your analysis and investigation, as detailed in the report.




<table width="473">

 <tbody>

  <tr>

   <td width="416"><strong>Rough/General Rubric for Marking of Assignment 1  </strong></td>

   <td width="57"></td>

  </tr>

  <tr>

   <td width="416">Item</td>

   <td width="57">Marks</td>

  </tr>

  <tr>

   <td width="416">Code – conforms to specification, code correctness, timing, style and comments</td>

   <td width="57">40</td>

  </tr>

  <tr>

   <td width="416">Documentation – all aspects required in the assignment brief are covered, e.g. Introduction, Methods, Results (with graphs and analysis), Conclusions.</td>

   <td width="57">50</td>

  </tr>

  <tr>

   <td width="416">Going the extra mile – excellence/thoroughness/extra work – e.g.additional investigations, depth of analysis, etc.</td>

   <td width="57">10 </td>

  </tr>

  <tr>

   <td width="416">Total</td>

   <td width="57">100</td>

  </tr>

  <tr>

   <td width="416">Code does not execute / run</td>

   <td width="57">-50</td>

  </tr>

  <tr>

   <td width="416">Code executes but no GIT repository</td>

   <td width="57">-20</td>

  </tr>

  <tr>

   <td width="416">GIT repository but no regular updates (at least on 5 separate days)</td>

   <td width="57">-15</td>

  </tr>

 </tbody>

</table>

Note: submitted code that does not run or does not pass standard test cases will result in a mark of zero. <strong>Any plagiarism, academic dishonesty, or falsifying of results reported will get a mark of 0 and be submitted to the university court</strong>.