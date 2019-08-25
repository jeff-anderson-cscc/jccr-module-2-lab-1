# Module 2 Lab 1 -- Classes and Interfaces

## Getting Started:

1. Clone or download a ZIP of this repository
1. If you downloaded a zip, extract the files to a working directory
1. Start IntelliJ and close any projects that reappear after opening
1. From the Welcome screen, choose "Open" navigating to the **top level** directory that contains the contents of this repository
1. When the message, "Maven projects need to be imported" appears in the bottom, right portion of the IntelliJ workspace, choose "Enable Auto-Import"
1. If necessary, open the "Project" pane so you can see the files under your new project

## Completing the Assignment

1. Move through each section below completing the steps indicated
2. Before moving on to the next section, open the *Module 2 Classes and Interfaces Lab Questions* assignment in Blackboard and answer the questions indicated

## Interfaces

### Defining Default methods

**Steps:**
1. _____ Under src > **main** > java > edu.cscc.jccr.module2, create an **interface** called ``BasicCalculator``
1. _____ Under src > **main** > java > edu.cscc.jccr.module2, create a **class** called ``TiCalculator`` that implements ``BasicCalculator``
1. _____ Under src > **main** > java > edu.cscc.jccr.module2, create a **class** called ``HpCalculator`` that implements ``BasicCalculator``
1. _____ In ``BasicCalculator``, create a *default* method ``String getModel ()`` that returns the String "Basic Calculator"
1. _____ Open ``HpCalculatorTests`` under src > **test** > java > edu.cscc.jccr.module2 and add the following code:
    ```java
      private final HpCalculator hpCalculator = new HpCalculator();
    
      @Test
      @DisplayName("T01: getModel() correctly")
      void getModelWorksCorrectlyTest() {
        assertEquals("Basic Calculator", hpCalculator.getModel(), "hpCalculator.getModel() should return \"Basic Calculator\"");
      }
    ```
1. _____ Right click on HpCalculatorTests and choose Run 'HpCalculatorTests' verifying your first test passes 

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q1. Defining Default methods -- True or false: Immediately after competing the steps above, ``TiCalculator`` will also return "Basic Calculator"
* Q2. Defining Default methods -- Given your answer on Q1 above, why or why not?

### Implementing Default Methods

**Steps:**
1. _____ Open ``TiCalculatorTests`` under src > **test** > java > edu.cscc.jccr.module2 and add the following code:
    ```java
      private final TiCalculator tiCalculator = new TiCalculator();
    
      @Test
      @DisplayName("T01: getModel() correctly")
      void getModelWorksCorrectlyTest() {
        assertEquals("Texas Instruments Calculator", tiCalculator.getModel(), "tiCalculator.getModel() should return \"Texas Instruments Calculator\"");
      }
    ```
1. _____ Right click on TiCalculatorTests and choose Run 'TiCalculatorTests' verifying this test **fails** 
1. _____ Implement ``String getModel ()`` method in ``TiCalculator`` having it return "Texas Instruments Calculator"
1. _____ Rerun the test from step 2, making sure it succeeds this time

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q3. Implementing Default Methods -- After you completed the steps above for implementing Default Methods, what string will ``HpCalculator.getModel()`` return?
* Q4. Implementing Default Methods -- After you completed the steps above for implementing Default Methods, how can you make ``HpCalculator.getModel()`` return something different?
* Q5. Implementing Default Methods -- What are the **benefits** of using a ``default`` method in an interface?
* Q6. Implementing Default Methods -- What are the **limitations** of using a ``default`` method in an interface?


### Implementing Interface Methods

**Steps:**
1. _____ Under src > **main** > java > edu.cscc.jccr.module2, create an **interface** called ``ScientificCalculator``
1. _____ Add the following method: ``public int square (int number)`` to ``ScientificCalculator`` 
1. _____ Have ``TiCalculator`` implement both ``BasicCalculator`` and ``ScientificCalculator``
1. _____ Implement the ``square`` method in TiCalculator having it ``return number * number``
1. _____ In ``TiCalculatorTests``, and add the following code:
    ```java
      @Test
      @DisplayName("T02: square() works correctly")
      void squareWorksCorrectlyTest() {
        assertEquals(25, tiCalculator.square(5), "5 squared should be 25");
        assertEquals(16, tiCalculator.square(4), "4 squared should be 16");
      }
    ```

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q7. Implementing Interface Methods -- True or false: After you complete the steps in Implementing Interface Methods, you could add the square works correctly test to HpCalculatorTests
* Q8. Implementing Interface Methods -- Given your answer to Q7 above, explain why you can or cannot.﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿﻿


## Inheritance

### Creating and Using a Superclass

**Steps:**
1. _____ Under src > **main** > java > edu.cscc.jccr.module2, create a **class** called ``BaseCalculator``
1. _____ Add the following method: ``public int addNumbers (int n1, int n2)`` having it  ``return n1 + n2`` 
1. _____ Have ``HpCalculator`` extend ``BaseCalculator``
1. _____ Have ``TiCalculator`` extend ``BaseCalculator``
1. _____ Open ``HpCalculatorTests`` under src > **test** > java > edu.cscc.jccr.module2 and add the following code:
    ```java
      @Test
      @DisplayName("T02: addNumbers(int, int) works correctly")
      void addTwoIntsWorksCorrectlyTest() {
        assertEquals(2, hpCalculator.addNumbers(1, 1), "1 + 1 should equal 2");
        assertEquals(5, hpCalculator.addNumbers(3, 2), "3 + 2 should equal 5");
      }
    ```
1. _____ Run ``HpCalculatorTests`` making sure all tests pass
1. _____ Open ``TiCalculatorTests`` under src > **test** > java > edu.cscc.jccr.module2 and add the following code:
    ```java
      @Test
      @DisplayName("T03: addNumbers(int, int) works correctly")
      void addTwoIntsWorksCorrectlyTest() {
        assertEquals(2, tiCalculator.addNumbers(1, 1), "1 + 1 should equal 2");
        assertEquals(5, tiCalculator.addNumbers(3, 2), "3 + 2 should equal 5");
      }
    ```
1. _____ Run ``TiCalculatorTests`` making sure all tests pass

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q9. Creating and Using a Superclass -- Since neither ``HpCalculator`` or ``TiCalculator`` define an ``addNumbers()`` method, how is it that the new tests added to ``HpCalculatorTests`` and ``TiCalculatorTests`` are passing?


### Abstract Classes

**Steps:**
1. _____ Create an ``abstract`` method in ``BaseCalculator`` called ``getSupportInfo`` that takes no parameters and returns ``String``
1. _____ Change ``BaseCalculator`` to be ``abstract`` 
1. _____ Add the new method to ``HpCalculator`` and ``TiCalculator`` having them return "hp.com" and "ti.com" respectively
1. _____ Below the last test in ``HpCalculatorTests``, add the following:
    ```java
      @Test
      @DisplayName("T03: getSupportInfo() works correctly")
      void getSupportInfoWorksCorrectlyTest() {
        assertEquals("hp.com", hpCalculator.getSupportInfo(), "hpCalculator.getSupportInfo() should return \"hp.com\"");
      }
    ```
1. _____ Rerun ``HpCalculatorTests`` making sure all tests pass
1. _____ Below the last test in ``TiCalculatorTests``, add the following:
    ```java
      @Test
      @DisplayName("T04: getSupportInfo() works correctly")
      void getSupportInfoWorksCorrectlyTest() {
        assertEquals("ti.com", tiCalculator.getSupportInfo(), "tiCalculator.getSupportInfo() should return \"ti.com\"");
      }
    ``` 
1._____ Rerun ``TiCalculatorTests`` making sure all tests pass
    
**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q10. Abstract Classes -- Immediately after adding the abstract method to ``BaseCalculator``, what compilation errors did you have to fix? 
* Q11. Abstract Classes -- What are abstract methods reminiscent of?
* Q12. Abstract Classes -- Why are abstract classes useful?

## Overloading Methods

![BaseCalculator class diagram](images/BaseCalculatorClassDiagram.png "BaseCalculator class diagram")

**Steps:**
1. _____ Open ``BaseCalculatorTests`` and add the following:
    ```java
      BaseCalculator baseCalculator = new HpCalculator();
    
      @Test
      @DisplayName("T01: add (int, int, int) works correctly")
      void addThreeIntsWorksCorrectlyTest() {
        assertEquals(3, baseCalculator.addNumbers(1, 1, 1), "1 + 1 + 1 should equal 3");
        assertEquals(10, baseCalculator.addNumbers(3, 2, 5), "3 + 2 + 5 should equal 10");
      }
    
      @Test
      @DisplayName("T02: add (double, double) works correctly")
      void addTwoDoublesWorksCorrectlyTest() {
        assertEquals(2.0, baseCalculator.addNumbers(1.0, 1.0), "1.0 + 1.0 should equal 2.0");
        assertEquals(5.5, baseCalculator.addNumbers(3.25, 2.25), "3.25 + 2.25 should equal 5.5");
      }
    
      @Test
      @DisplayName("T03: add (double, double, double) works correctly")
      void addThreeDoublesWorksCorrectlyTest() {
        assertEquals(4.5, baseCalculator.addNumbers(1.5, 1.5, 1.5), "1.5 + 1.5 + 1.5 should equal 4.5");
      }
    ```
1. _____ in ``BaseCalculator``, add and implement the additional ``addNumbers`` methods shown in the class diagram above so your new tests will pass
1. _____ Rerun ``BaseCalculatorTests`` making sure all tests pass

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q13. Overloading Methods -- With four ``addNumbers`` methods in ``BaseCalculator``, How does Java know which one to invoke?
* Q14. Overloading Methods -- In the tests you added above to ``BaseCalculatorTests``, why does the test create a new instance of ``HpCalculator`` instead of ``BaseCalculator``? 

## Variable Arguments

![BaseCalculator class diagram](images/BaseCalculatorClassDiagram.png "BaseCalculator class diagram")

**Steps:**
1. _____ Below the last test in ``BaseCalculatorTests``, add the following:
    ```java
      @Test
      @DisplayName("T04: multiplyNumbers(double... numbers) works correctly")
      void multiplyNumbersWorksCorrectlyTest() {
        assertEquals(0, baseCalculator.multiplyNumbers(), "nothing to multiply should equal 0");
        assertEquals(5, baseCalculator.multiplyNumbers(5), "5 * nothing should equal 5");
        assertEquals(10, baseCalculator.multiplyNumbers(10), "10 * nothing should equal 10");
        assertEquals(2, baseCalculator.multiplyNumbers(1, 2), "1 * 2 should equal 2");
        assertEquals(6, baseCalculator.multiplyNumbers(1, 2, 3), "1 * 2 * 3 should equal 6");
      }
    ```
1. _____ in ``BaseCalculator``, add and implement the ``multiplyNumbers`` method shown in the class diagram above
1. _____ Rerun ``BaseCalculatorTests`` making sure all tests pass

**Questions:**

Answer the following questions in Blackboard, *Group Lab: Module 2 -- Part 2 Questions*:

* Q15. Variable Arguments -- How can you use variable arguments to simplify ``BaseCalculator``?

**Bonus Assignment:** use this technique to simplify ``BaseCalculator`` making sure the tests still pass. 