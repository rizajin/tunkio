## Part 2: Creating a Custom Testing Framework and Implementing Image Comparison API

In the previous part of this test case, I discussed the importance of various testing structures, such as unit tests, BDD, visual testing, and development-time debug APIs, in ensuring high-quality software. I also introduced TDD within BDD and the benefits of combining the two.

In this part, I will discuss the implementation of a custom testing framework and the integration of an image comparison API to enhance visual testing. Additionally, I will provide an overview of the simplified calculator application used for testing the custom framework and the upcoming BDD part of this test case.

### Custom Testing Framework
As mentioned in the previous part, I decided to develop my own testing framework instead of using an existing one like gtest. By doing this, I gain full control over the framework's implementation, allowing me to customize it to meet my specific needs.

My custom testing framework is built from scratch and provides a basic set of features such as test cases, test suites, and assertions. I have integrated the image comparison API into the framework to enhance my visual testing capabilities.

### Using a Function-Based Approach Instead of Macros
```c++
ITestFw * testFw = createTestFw("Series 2 breakdowns");

testFw->addTest("Addition Test", additionTest);
testFw->addTest("String Test", stringTest);
testFw->addTest("Failing Test", failingTest);

testFw->run();
testFw->printResults();
```
In my custom testing framework, I chose to use a function-based approach for adding and running tests instead of macros like TEST(bigbicture, test). The reason behind this decision is that macros have global scope and can potentially conflict with other macros or identifiers in your code. Moreover, heavy reliance on global constructs is often considered a legacy practice in modern C++ programming, which applies to test frameworks too. ;D

By using a function-based approach, I can avoid these issues while still maintaining a clean and easy-to-understand testing structure. This method also provides better control over test execution and results reporting, as well as improved encapsulation of test cases within the custom framework.

### Image Comparison API
Visual testing is an essential part of software testing, as it ensures that software meets user needs in terms of appearance and usability. However, traditional visual testing methods like manual inspection or screenshot comparison can be time-consuming and error-prone.

To enhance visual testing, I have implemented a basic image comparison API that compares two images and returns a similarity score. In cases where the images differ, a difference image is returned. The API uses pixel comparison to compare images and calculates a score based on the number of matching pixels.

The image comparison API allows me to automate visual testing and detect visual defects that functional or unit testing may miss. By integrating the API into my custom testing framework, I can further enhance my testing capabilities.

### Simplified Calculator Application
For the purposes of testing my custom framework and upcoming BDD implementation, I have created a simplified calculator application. The calculator application includes only the UI part, which does not perform any actual arithmetic operations. I included this application to showcase the image comparison test capabilities.

I plan to use the calculator application as a "test" application for the framework, where I can write test cases to ensure the application functions correctly. Additionally, in the upcoming Part 3 of this test case study, I will discuss the BDD implementation in more detail for the calculator application and integrate the BDD framework.

Furthermore, I plan to develop a development-time debug API, which I might call the Command/s API, to assist with recording events, tracking software execution, identifying and fixing defects during development. This will likely be a two-way solution, but the exact implementation remains to be seen.

### Conclusion
In this part of the test case, I discussed the implementation of a custom testing framework and the integration of an image comparison API to enhance visual testing. I also introduced the simplified calculator application used for testing the custom framework and upcoming BDD implementation. Additionally, I highlighted the benefits of using a function-based approach over macros in my custom testing framework.

By developing my custom testing framework, I have full control over the testing process, allowing me to customize it to meet my specific needs. Furthermore, the image comparison API enhances my visual testing capabilities, enabling me to automate the testing process and detect visual defects more efficiently.

In the next part of this test case, I will discuss the BDD implementation for the simplified calculator application and potentially integrate a BDD framework or testing suite. I will also introduce the development-time debug API, which will assist in identifying and fixing defects during development.

### Future thoughts at this moment
As of writing, I have been considering what other possible features this project could have, and there are a few options. One idea worth mentioning could be a Python API.

### Disclaimer: I won't share much more than this (maybe the part3 share?), as it's in a WIP state, so enjoy the video instead.

[![Lets make testing great again!](https://img.youtube.com/vi/EBt353tmwF0/0.jpg)](https://www.youtube.com/watch?v=EBt353tmwF0)
