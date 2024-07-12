##### Testing vs Debugging
Software testing is the process of checking that your software application meets the expected requirements, and to make sure it is defect free.
Debugging is the process of locating and resolving bugs.

##### Debugging Process Phases
![[Pasted image 20240710134038.png]]

##### 1. Stabilization
This is usually called reproduction. Mainly the goal of this phase is to be able to reproduce the error on a particular configuration, and to find out the conditions that led to the error by constructing a minimal test case. You do not need to locate the issue in the code in this phase. You just need to identify which input conditions, combined with which program states, produce the error . The output of the stabilization phase is test case(s) that produce the error.

##### 2. Localization
The process of localization involves finding the section(s) of the code that led to the error. Usually, it is the hardest part, although, if the stabilization phase produces a very simple test case, it may make the problem obvious.

##### 3. Correction
The process of correction involves modifying the code to fix the errors. If you understand what caused the error, you have a good chance of fixing the issue. A common mistake is to try to correct the problem without having really stabilized it or located it within the source code, which leads to random changes that do not fix the code and may introduce new errors.

##### 4. Verification
In this process you should make sure the error is fixed, and no other errors were introduced with the changes in the code. Many times, a change in the code will not fix the error or may introduce new errors. It is better that you add unit test(s) since you changed the code.

##### Tips for Stabilizing the Error
- You need to be able to reproduce the problem!! 
	- Some issues can be easily reproduced. 
	- Some issues are harder to reproduce … some possible reasons for randomness preventing the reproduction of the problem.
 In order to help reproduce, we sometimes need to simplify the environment as much as possible 
	- Then, change the environment and see how the behavior changes.
	- As an example, when trying to replicate a reported customer error you need to be aware of the H/W differences, O/S (and patch) differences, other S/W installed on the systems 
	- By doing this, you can eliminate various factors until the number of possible factors left are manageable
	
##### Tips for Finding Defects
- Source code comparators that can help you quickly find changes to the code. 
- Interactive debuggers that let you examine variables, step over certain points in your code, and establish breakpoints and interrupt the program at particular places. 
- Brainstorm for possible hypotheses 
- Use other developers, blogs, articles as sources of information to give you ideas 
- Narrow the suspicious region of the code. Be suspicious of routines that have had defects before.

##### Tips on FIXING Defects
- Before you fix it – make sure you understand the problem 
	- Understand the program, not just the problem 
	- Confirm the defect diagnosis 
- Save the original source code 
	- Make a copy – just in case you need to back-out a change you made 
- Change the code only for good reason - Don't make changes using trial and-error
- Make one change at a time and check if the defect has been solved