****SENG 637 - Dependability and Reliability of Software Systems****

**Lab. Report \#5 – Software Reliability Assessment**

| Group \#:       |   |
|-----------------|---|
| Jay Kanabar     |   |
| Andrew Bright   |   |
| Jahnavi Akuri   |   |
| Hetalben Virani |   |

# Introduction

The purpose of this lab is to explore the different analysis of integration test data using reliability assessment tools. Two methods exist for evaluating failure data:1) Reliability growth testing 2) Reliability assessment using Reliability Demonstration Chart (RDC). With the use of these tools, it is possible to evaluate a hypothetical system's dependability using failure information gathered during integration testing. Also, it would be possible to measure the failure rate, MTTF and reliability of the SUT through analyzing the test data.

1) Reliability growth testing - C-SFRAT
By testing and analysis, reliability growth testing helps to increase a system's dependability. Testing for reliability growth aims to find and remove failure-causing factors while also raising the system's overall reliability.
The methodology is applied to crucial subsystems within a larger system in the context of C-SFRAT reliability growth testing, using fault-tree analysis to identify possible failures and their causes. Then, these subsystems are tested and made more reliable using the reliability growth testing procedure.



**Models in C-SFRAT**
The C-SFRAT provides various models with Accuracy,Bias,Moise and Trend Analysis 

Geometric 
Jelinski/Moranda De-Eutrophication 
Littlewood and Varral's Bayesian Reliability
John Musa's Basic Exceution Time
John Musa's Logarithmic Poisson
Non-homogeneous Poisson 


### **Geometric Model**
This model shows the accept ,reject and failure data based on the given range of Discrimation ratio,Customer risk,Developer risk values.


![plot](/media/geometric_model.png)



**Jelinski/Moranda De-Eutrophication**
This model throws Java.lang.Exception as shown below


**John Musa's Basic Exceution Time**
This model throws Java.lang.UnsatisifiedLinkError as shown below


**John Musa's Logarithmic Poisson**
This method throws java.lang.NullPointerException as shown below

**Effect of Start and End index values on Model_result,Accuracy and Prediction Results**

Executing the models with Default start and end indices (14,28)

Exceuting the models with customized start and end indices (20,30)

 To conclude,Geometric model suits well for the given data in comparison to other models

2) Reliability assessment using Reliability Demonstration Chart (RDC)
A graphical tool called a reliability demonstration chart (RDC) is used in reliability engineering to show that a system or product satisfies a given reliability criterion. During reliability testing, the RDC is utilised to monitor the frequency of failures over time and to contrast the observed failure rate with the desired failure rate.
The RDC normally consists of a graph with two axes: the horizontal axis displays the cumulative test time or test unit count, and the vertical axis displays the cumulative number of failures. The reliability requirement line, which represents the required dependability level as a horizontal line on the graph, is also included.
Failures are noted and displayed on the RDC during testing. The product or system is deemed to have met the reliability requirement if the measured failure rate is below the reliability requirement line. More testing or design modifications can be required to increase the dependability of the system or product if the reported failure rate is higher than the reliability requirement line.

# Assessment Using Reliability Growth Testing 

### Initial data (J2.dat)
![CS_J2_1](/media/CS_J2_tab1.PNG)

### Initial data (J2.dat) intensity view
![CS_J2_1](/media/CS_J2_tab1_int.PNG)

### Model evaluation (J2.dat)
As seen below, the Discrete Weibull Type III (DW3) model fits our given data the best.
![CS_J2_1](/media/CS_J2_tab2.PNG)

### Model evaluation (J2.dat) intensity view
Compared to the previous view, the Discrete Weibull Type III (DW3) model matches the peaks the best. This shows it is still the best model when evaluated in the intensity view.
![CS_J2_1](/media/CS_J2_tab2_int.PNG)

### Model comparisons (J2.dat)
The numerical values concur with the visual conclusions in the previous images. As seen in the table, the DW3 model has:

- lowest log likelihood
- lowest AIC, BIC, SSE
- highest critic (mean, median)

This once again shows that the DW3 model is the best fit for the J2.dat file.

![CS_J2_3](/media/CS_J2_tab3.PNG)

# Assessment Using Reliability Demonstration Chart 

### MTTF_min value for J2.dat
This represents the minimum "mean time to failure" and how the tested data passes
![MTTF min](/media/G17_MTTF_min.PNG)

### Half MTTF_min value for J2.dat
This shows the trend when the requirement is failures happening in half the time (twice as often) which means the requirement is much looser, and worse software will pass. This is shown by the large green zone.
![MTTF min half](/media/G17_MTTF_min_half.PNG)

### Double MTTF_min value for J2.dat
This shows the trend when the requirement is failures happening in double the time (half as often) which means the requirement is much tighter, and only better software will pass. This is shown by the large red zone which our tested data falls inside.
![MTTF min double](/media/G17_MTTF_min_double.PNG)

# Comparison of Results

- The time between failures is getting longer near the end of the data range, which suggests the reliability is getting better. But, in RDC, the cumulative data region denotes the dependability factor, i.e., the SUT is acceptable/reject/continue, based on the MTTF value.
- Also, we could forecast the system's dependability for the minutes to come, which the RDC technique cannot do.
- Due to the short dataset, RDC is more trustworthy than reliability growth analysis.
- The RDC method decides whether or not this programme is reliable, accepts or rejects the current system, or needs more data to decide. It works similarly to a classification problem. Nonetheless, reliability growth testing functions somewhat similarly to a regression problem in that it forecasts future reliability, failure rate, and duration between failures.
- With the use of the reliability growth study, we discovered that the present failure rate, which is around 0.33 per minute, is unacceptable when compared to the desired failure rate of 0.01. If the trend continues, we could forecast when we would attain this goal. Contrarily, RDC performs this computation on its own behalf using the risk inputs (Developer's Risk and Users Risk) that we provide to the system.

# A discussion on decision making given a target failure rate

The failure rate in our dataset is approximately 0.33 failures per minute, as you can see in the last figure up top. (total failures / overall instances). According to the course lectures, achieving (the failure rate / goal failure rate) 0.5 is sufficient for product release. The system does not meet the requirement if we use 0.01 as the target failure rate because the existing failure rate is higher than this value. Yet, with a lower failure rate, we can still achieve our goal, while significant system upgrades are required. It is important to note that our model is insufficiently accurate due to the tiny size of our dataset.

# A discussion on the advantages and disadvantages of reliability growth analysis
A technique called reliability growth analysis is used to monitor and enhance a system's or product's reliability over time. To predict future failure rates and increase reliability, it entails gathering data on errors and the corrective measures that were done.

Advantages of reliability growth analysis:
1) Early on in the product development process, it assists in identifying and addressing potential problems, which can help save time and resources.
2) It enables ongoing product optimisation and enhancement by monitoring failure rates over time.
3) It offers insightful information on a system's or product's dependability, which can guide choices regarding warranties, maintenance schedules, and other crucial aspects.
4) It can assist firms in fulfilling safety and dependability regulatory standards.

Disadvantages of reliability growth analysis:
1) The process of gathering and processing the required data can be time- and resource-consuming.
2) To effectively evaluate the data, one must have a good level of statistical knowledge.
3) It might not be suitable for all systems or products, especially those with extremely low failure rates or complicated failure modes.
4) It is predicated on the idea that remedial measures will genuinely increase reliability, which may or may not be the case.

# A discussion on the advantages and disadvantages of RDC
In engineering and product development, reliability demonstration charts—also called reliability growth charts—are frequently used to monitor a product's reliability over time. These graphs can offer insightful information on a product's dependability and aid in the early detection of potential faults. Yet, employing dependability demonstration charts has both benefits and drawbacks.

Advantages:
1) Predictive tool
2) Improvement tracking
3) Communication
4) Data visualization

Disadvantages:
1) Limited scope
2) Limited accuracy
3) Subjectivity
4) Time-consuming

# Discussion on Similarity and Differences of the Two Techniques

Similarities:

1) Both methods are used to evaluate a system's or product's dependability.
2) Both methods need the gathering and analysis of data.
3) The efficacy of process or design changes can be assessed using any of these two methods.

Differences:

1) A technique called reliability growth analysis is used to evaluate how much a system or product's reliability has increased over time. To do this, data on failures must be gathered, analysed, and process or design adjustments must be made to address the root causes of those failures. The objective is to reduce the number of failures over time in order to reach the target degree of reliability.
2) Contrarily, a reliability demonstration chart is a method used to show that a system or product satisfies a predetermined degree of reliability. This is accomplished by performing tests on a sample of the system or product and proving that it satisfies the required level of reliability.
3) A single test to show that a system or product satisfies a predetermined level of reliability is used in reliability demonstration charts, but reliability growth analysis often entails a continual process of monitoring, analysing, and increasing reliability.
4) While reliability demonstration charts are typically used towards the end of the development process to show that the product or system meets the required level of reliability, reliability growth analysis can be used throughout the product development process to identify and address reliability issues.

# How the team work/effort was divided and managed

Microsoft Teams served as our primary means of contact, and Zoom was used for both video conversations and recording the demo. We all concentrated each and every parts in order to minimize challenges during testing as we all assisted to eachother. We later double-checked our findings and distributed the report amongst ourselves.

# Difficulties encountered, challenges overcome, and lessons learned

The absence of testing tools like manual testing or unit testing made this task different from other labs. Instead, in order to suit failure diagrams, we must employ new technologies. It took a lot of effort to figure out how to use various tools and to discover the one that meets all of our requirements.

We had trouble using the RDC excel sheet. Several functionalities wouldn't function as planned. For instance, we were unable to modify the graph's limits in order to accurately capture the data points. Also, we were unable to change the limits for "Acceptance," "Continue," and "Reject." We spent a lot of effort attempting to get the antiquated and unreliable excel to function properly, but in the end, we had to hardcode the MTTFmin number in order to show it on the graph.

Overall, 3 of the 4 provided tools did not work. The RDC tool in particular was very bad, and the structure of the excel sheet suggests it had been abandoned long before this lab was assigned. Many of the cells were hardcoded and unexplained values which made it impossible to graph our data without completely overhauling the structure of several sheets. Even after doing so, the logical links between items were incorrect and made it extremely difficult and tedious to accomplish the lab tasks.

# Comments/feedback on the lab itself
This lab was useful for learning about various analysis of integration test data using reliability assessment tools as well as how to use GitHub issues. The rubric/report structure offered a simple approach to structure the report, and the lab instructions were comprehensive enough to provide the team with guidance on how to finish the lab.

Unfortunately, all of the tools and information in the lab were extremely outdated which contributed to an enormous amount of difficulties for our team, none of which offered useful or practical experience in the end. They were frustrating to fix, wasted time, and ultimately should have been addressed and fixed before this lab was assigned to students. With much of the software, new computer platforms and data formats were completely unsupported, as one macOS user in the group found out. The time spent on these roadblocks could have been spent on testing and designing software instead, or learning newer frameworks which are relevant in the workplace.

![old](/media/cutting%20edge.PNG)

As seen above, the provided data is older than many enrolled students.
