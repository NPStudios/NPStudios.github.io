---
layout: page
title: Testing
permalink: /testing/
nav_order: 6
---

# Testing Documentation for Assessment 2 and 3
This section provides the testing design (from tracability matrix to test documentation) and also links to the most up-to-date test coverage of the game for each Assessment!

## Assessment 2
### Test Design:
> * Tracability Matrix: [PDF](/files/tracability_matrix.pdf)
> * Test Documentation: [PDF](/files/test_documentation.pdf)

### Evidence of Testing: 
> * To find latest testing: Go to [zipped](https://drive.google.com/file/d/1H4JW_dwoqctEgOOuH97xNl6Nck0H5exh/view?usp=sharing) file, download and use the code provided, under /core/test is where the tests are. To run these test in one go, left click the /core/test/java file and run it! [See Image](/files/how_to_test.png)


## Assessment 3
### DicyCat's tough to test code
As mentioned in the 'Change' report, the testing team encounted various hurdles when trying to test DicyCat's code. Speficially the error that needed the most effort to resolve was centred around the line ‘Kroy.mainGameScreen. …’.

This NullPointerException error is due to the overall project architecture and structure of various classes, like ‘FireTruck’, which have a super call in their constructor which requires ‘Kroy.mainGameScreen. …’. This needs the headless test runner to instantiate the two static classes Kroy utilizes - mainGameScreen and mainMenuScreen, which it cannot not. 

A solution we looked into was to mock these classes, however since they are never passed as variables we can’t get the mocked versions through. Alongside this issue, the classes are defined as static in the Kroy class, which Mockito struggles to handle. After trying to fix these issues using PowerMock to handle static declarations - which still left the problem of a never instantiated mainGameScreen or mainMenuScreen, and trying with different headless structures, we came to a decision. 

It was to create an alternate code base where the testing team would slightly alter the code to allow for the classes to be tested. Any class that did not need altering, like GameObject or Entity, have their tests in both the main code base and the altered code base. We ensured that all changes made were to non-functional aspects of the classes, like GUI or camera viewing. This way we are sure that the tests still cover relevent code and through intergation testsing and mocking we have a strong test suite. 
	
To keep track of the changes being made we kept a table with names for changes, which class they are in, and a description of why these changes were being made. Both sets of tests, on the main code base and altered, are included the the testing design and other testing documentation.  
### Documentation: 
> * Tracebility Matrix: [PDF](/files/Assessment3_TestDocuments/UserRequirementTraceabilityMatrix.pdf)
> * Testing Design and Documenation: [PDF](/files/Assessment3_TestDocuments/TestDesignandDocumentation.pdf)

### Statistics: 
> * Individual Test Duration: [HTML](/files/Assessment3_TestDocuments/Specific_Test_Stats.html)
> * Overall Test Analytics: [HTML](/files/Assessment3_TestDocuments/index.html)

### Run Tests: 
> * Insdide the main root folder there is a 'tests' folder, left click and press 'Run ...' to run all tests! [See Image]()
