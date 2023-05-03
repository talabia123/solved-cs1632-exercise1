Download Link: https://assignmentchef.com/product/solved-cs1632-exercise1
<br>
For this exercise, you and your partner will determine a test plan for thesimple simulator GoatGoatCar, based on the requirements listed. There shouldbe at least 6 test cases altogether. Test cases should mention all necessarypreconditions, execution steps, and postconditions. Additionally, atraceability matrix showing the mapping of test cases to requirements isrequired.

There are several known defects in the software (10 at last count); try to find andreport on at least two.

It is expected that you execute the test plan in order to find the defects, butyou may find it useful to initially do some exploratory testing to determinehow the system works. While you are not expected to find *all* of the defects,a reasonable test plan should definitely find at least two. This is anintentionally target-rich environment.

You may ask me any questions you may have during class. It’s not scored. Ask me anything.

## Creating a Test Plan

Remember, the template for test cases –

“`IDENTIFIER: [A unique number or string (e.g. TEST-ARGS-NUMBER-FIVE-ARGS)]TEST CASE: [A description of the test case]PRECONDITIONS: [State of the system before performing execution steps]EXECUTION STEPS: [Steps to perform test]POSTCONDITIONS: [ *EXPECTED* state of the system after performing execution steps]“`

The IDENTIFIER is some value which will uniquely specify the test case. Welearned it can be either a number, or a more descriptive label (e.g.TEST-INVALID-TIMES, TEST-LOW-NUM-TIMES, etc.). For this exercise, please use adescriptive label. Note that the INPUT VALUES and OUTPUT VALUES fields in thetemplate are omitted because we are not doing method unit testing.Please refer to [Lecture 4: Test Plans](../../lectures/CS1632_Lecture4_Test_Plans.pdf) Slides 8 – 13for more details and examples for each item.

PRECONDITIONS is the state of the system before performing the test. If thesystem is a website, it is things like: “user is logged into the website” or“user is subscribed to the mailing list”, etc. The program we will be testingtoday is a commandline Java program where the test is simply running theprogram with a set of arguments. There is no program state to speak of beforerunning the test. Then, what things should you put as preconditions? Thereare plenty! For a Java program, it is always important which Java RuntimeEnvironment (JRE) the program runs in. You could say something like: When“java -version” is run, the system outputs “java version “1.8.0_231”.Companies would actually perform multiple tests using the same arguments formultiple versions of Java that their clients use, and each would be a separatetest case!

EXECUTION STEPS should be numbered step-by-step instructions on what you expectthe tester to do. It should be exact to the letter so that tests arereproducible. The tested program does not allow any interaction with the userother than to run it with commandline arguments, so all steps will beone-liners in this case, but typically there will be multiple steps.

POSTCONDITIONS should be the **expected** state of the program after the test.It is **not** the observed state. So where should you get expectations of yourprogram? From the [requirements](requirements.md) of course!

## Creating a Traceability Matrix

A traceability matrix allows us to correlate test cases to requirements andvice versa. It allows us to check why a test case is being run (to check oneor more requirements). It also allows us to check how much testing aparticular requirement is receiving. See Chapter 6 section 6 (6.6) in thetextbook for examples and details on creating them.

Note that some test cases may test several requirements at once. This is onlynatural. As we saw on the last example on the lecture slides, in a real-worldtraceability matrix, you can have one test case mapped to multiplerequirements. Vice versa, you can have several test cases for one requirement.

Also note that a good traceability matrix must cover all requirements to haveno gaps in test coverage. Please make sure of this.

## Reporting Defects

Please listen to “Lecture 5: Defects” before completing this section.

This is the correct format for defects –

“`IDENTIFIER: [A unique number or string (e.g. BUG-ARGS-NUMBER-FIVE-ARGS)]SUMMARY: [A one sentence description of defect]DESCRIPTION: [A detailed description of everything the tester discovered]REPRODUCTION STEPS: [Preconditions + Steps to reproduce (similar to test case execution steps)]EXPECTED BEHAVIOR: [What you expected according to requirements]OBSERVED BEHAVIOR: [What you *ACTUALLY* saw]“`

Please refer to [Lecture 5: Defects](../../lectures/CS1632_Lecture5_Defects.pdf) Slides 15 – 22for more details and examples for each item. Optional bug report itemssuch as SEVERITY or IMPACT were not included for this exercise.

**Don’t forget to include any preconditions at the start of the REPRODUCTIONSTEPS.** You will not be able to reproduce the bug even if you reproduce thesteps if you start from a different precondition!

## Test Application: GoatGoatCar

GoatGoatCar is going to be our way of determining the correct answer to the“Monty Hall Problem” (https://en.wikipedia.org/wiki/Monty_Hall_problem). TheMonty Hall Problem can be summarized in pictures:

&lt;img alt=”Figure 1″ src=img/monty-hall-pic-1.jpg width=350&gt;&lt;img alt=”Figure 2″ src=img/monty-hall-pic-2.jpg width=350&gt;&lt;img alt=”Figure 3″ src=img/monty-hall-pic-3.jpg width=350&gt;&lt;img alt=”Figure 4″ src=img/monty-hall-pic-4.jpg width=350&gt;&lt;img alt=”Figure 5″ src=img/monty-hall-pic-5.jpg width=350&gt;

What do you think? The answer lies in the below illustration:

&lt;img alt=”Figure 6″ src=img/monty-hall-pic-6.svg width=350&gt;

If you still don’t get it, you can read the above wikipedia entry if you likereading, or here is a video if you are a more visual learner: https://www.youtube.com/watch?v=9vRUxbzJZ9Y.

Another way to get at the answer is through Monte Carlo simulations, that issimulate the game thousands of times to empirically answer the question oneway or another. The program we will test today randomly generates games,plays them one way another, and gives a summary at the end of what percentageof the time switching would give you the “good item” and what percentage ofthe time staying would have won you the “bad” item.

The program will accept four arguments, in this order:

* __”Good” option__ – This will be the item that the player actually wants (e.g., a car).

* __”Bad” option__ – This will be the item that the player does not want (e.g., a goat)

* __Num Times__ – This is the number of rounds that will be simulated.

* __Num Threads__ – This will be the number of threads that the simulation runs in

Example command to execute. This will use “car” as the good choice, “goat” asthe bad choice, 10001 as the number of rounds to simulate, and it will do it onfour threads.

“`$ java -jar GoatGoatCar.jar car goat 10001 4“`

GoatGoatCar.jar is available in this directory.

Create a reasonable test plan based on the [requirements](requirements.md).Hint: Try to have a combination of explicit boundary values and implicitboundary values as well as interior values in your test cases. As we learned,this is where most of the defects will reside!

## Submission

Please note that the submission of this exercise takes the place of theattendance check for this in-class exercise. Submission will be reflected onyour participation grade. As long as the submission shows any amount ofreasonable work was done (that is, you don’t get a 0 on GradeScope), it willcount. On the other hand, the actual score you get on GradeScope will notcount towards your grade. It’s there only for feedback purposes and help youdo Deliverable 1 better. This applies to all future exercises.

Please use the ReportTemplate.docx file provided in this directory to writeyour report. If you don’t have a .docx compatible word processor, that’sperfectly fine as long as you follow the same organization. A PDF version ofthe file is at ReportTemplate.pdf. Please make sure that the traceabilitymatrix, test cases, and defects are on seperate pages. You will be submittingto GradeScope in PDF format. When you submit, you will be asked to assignpages in the PDF file to each rubric item: 1. Traceability Matrix, 2. TestCases, and 3. Defects.

Each pairwise group will submit the exercise *once* to GradeScope to the**Exercise 1** link, by *one member* of the group. The submitting member willpress the “View or edit group” link at the top-right corner of the assignmentpage before or after submission to add his/her partner. That way, the feedbackwill be accessible to both of you.

When your exercise is marked as graded, you should find feedback written onyour grade details. Please use the feedback wisely when doing Deliverable 1!

* One quirk about submissions: the exercise on GradeScope is due on Wednesday butlate submission is allowed until Thursday. That is just a trick I’m using todifferentiate the two sections. The Mon/Wed class should still submit byWednesday 9:00 Am and the Thu/Thu class should still submit by Thursday 9:00AM.

## Extra Credit

* DUE: Sep 14, 2020 09:00 AM

This submission is optional. An extra credit of 1 point out of 100 points forthe entire course will be awarded to the group that finds the most number ofdefects in the program. There can be multiple winners too if there is a tie!

Duplicate defects that are really the same defect that is triggered by twodifferent inputs will be counted only once. How do you know if it is the samedefect? If they display the same behavior (e.g. causes the same type ofexception at the same source code line).

Also, some behaviors that you may think are defects are expected behaviors. Atbelow are some examples:

1. Bash behavior

“`$ java -jar GoatGoatCar.jar car goat 1000 &gt;“`… or …“`$ java -jar GoatGoatCar.jar car goat 1000 ”&gt;“`

This is just normal bash behavior that allows user to enter multi-linecommands. In the first case, the newline was escaped () and in the secondcase, a multi-line string was started using the quote(“) charater. Otherspecial characters recognized by bash is listed here:

https://www.tldp.org/LDP/abs/html/special-chars.html

2. Empty names or duplicate names

“`$ java -jar GoatGoatCar.jar “” “” 1000 4Thread 0: 250 iterations.Thread 1: 250 iterations.Thread 2: 250 iterations.Thread 3: 250 iterations.Calculating..

Switch:: 68.500%: 31.500%—————————–Stay:: 31.500%: 68.500%“`

There is no requirement that the “good” and “bad” strings have to beunique, or they cannot be empty strings for that matter. This is stillbehavior conformant with the requirements.

Each pairwise group will submit the exercise *once* to GradeScope to the**Exercise 1 Extra Credit** link, by *one member* of the group. Please use theReportTemplateExtraCredit.docx to write the report. Make sure you number thedefects so it is easy to count!