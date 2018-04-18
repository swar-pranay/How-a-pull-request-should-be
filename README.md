# How-a-pull-request-should-be
Basic checkpoints before submitting a pull request/ merge request for iOS development using Xcode and Swift/ObjC.

These checkpoints are not for the reviewer, but more for the person submitting the pull/merge request to have list to go through before finally raising the flag for 'ready for peer review'. 

- [x] Does the code compile for all relevant targets.  
I know this sounds rather obvious, but there are times when we would make this one line change or even one character change for some defect fix and don't really check to see of the code compiles. This is especially important if you add a new file/resource and forgot to assign target membership to all the relevant targets. 

- [x] Does the code compile cleanly without warnings/errors.   
This is to make sure that your changes did not add any new warnings to the code. By warnings/errors, I mean two types a) those given by the compiler. b) The warning/errors given by any other linting program that you could be using in your software development peocess. We use SwiftLint for Swift source code. This also makes sure the entire code base is in agreement with the set standards for styling and convention.

- [x] Not Errors/Warnings in Storyboard, View Debugger and console (waring in console for unsatisfiable layouts).    
This is again relevant to you if you have made even slightest of the changes related to User Interface. This check mark is to make sure to remove and fix those warnings/Erros (most likely because the constraints are not defined in the right way). View Debugger is again a great tool introduce in the recent years to Xcode and with Xcode 8.0 it detects the Ambigious layouts right in the view Debugger. Ambigious layouts are one of those things that you won't know about it until you know, because unlike Unsatidfiable layouts, it doesn't display it on cosole and goes undetected. With the view debugging tool, it has become easier to deal with it. Also, stating the obvious, before checking this point as good, its a good time to look at the console and see if the layout engine broke some constraint because of unsatisfiable layout. If yes, than the constraints should be defined in some other way. 

- [x] Static Analysis and Memory Graph Analysis.    
This is one of the overloked areas especially after introduction of ARC and with tools like Memory Graph Debugger, it has become much easier to find and detect leaks in your code. Although these tools might fails in detecting leaks sometime, they are great way to quickly scan the code and find the obvious ones. So, make sure you run the code through these. 

- [x] Used private and final where appropriate.   
By default all the members of the class/struct/enums are internal. But there could be instances where you want to hide members properties or methods for the purpose of abstraction or encapsulation, from someone who could potentially use your interface. This is the checkmark to make sure you comply to that. Also, marking the class as final help the compiler optimize and redcue the binary size. So, make sure to use the keyword and mark classes as final to indicate the compiler that this wont be inherted further. (until you actuall need to inherit it)

- [x] Remove unnecessary inferencing to Objective-C dispatch using @objc
This one is not so important, after Swift 4 stopped implictly adding @objc to all classes inherited from NSObject. But this checkmark is just there to double check that which helps in reducing the size of the binary. 

- [x] Runs as expected on all the size classes  
Size classes helps our UI adapt to the wide variety of idevice that exist. This is especially important when you are working on the User Interfact. However small change it may be, it may not necessarily work on other size classes. So, this check is just to make sure you have ran your code on all the different size classes. 

- [x] Unit test/ UI test added.  
This checkmark is for you to make sure that you have added good Unit and/or UI tests and/or snapshot tests for your changes and the test coverage for your newly added code is 100% (or close to 100%). I like to have long descriptive names for the text cases so that the name of the test becomes self explanatory and sort of acting as a documentation for the method under test.  

- [x] Unit test/UI test passed.  
Its is rather obvios habbit to make sure you run the entire test suite before you submit your changes to make sure you did not break any of the test. After all, those tests are written for these situaltions where you introduce a breaking change and you go and make changes to them to comply to these new changes. It is important here to make sure that the tests are ran against all relevant size classes. Running all unit/UI tests against all size classes is strongly recommended and is usually something that is ignored. 

- [x] Documents updated/Comments in code.  
Lot of the teams out there do add a lot of comments in code. Xcode has a nice feature to fold and un-fold the comments in a file. So, this particular check point is to make sure comments in code are taken care. A lot of the teams also do maintain a document wiki page for the project. This is a good method have some documentation with respect to the achitecture decisions made inside the application as well as all relevant decisions that were made in the past may that be decision to why go with a particular third party library. I feel doumentation is a very important aspect of any software development. Not only it helps any new developer quickly get on board, but also help current developers to go back and refer to the document to see why a particular feture was implemented in a particular way. Documentation can be in any form, It could be a simple text or it could even be a simple picture taken from your phone of a diagram that you have drawn on a piece of paper and uploaded or even links to other websites. Whatever that make explaning something about the project better will help in the long run and improve the effecieny of the Project. 


## Other Points 
- A code review can be conducted by the dev lead if he is not confortable in getting the changes into development without his supervision, or if the team gets seasoned over time, it can have multiple members doing the code review that way there is more sharing of ideas and best code practices. 

- I am a strong beleiver of having the best performance when it comes to the user experience. Afterall, performance is **A Feature**. Instruments is an awesome tool that comes along with Xcode and is one of the best tools out there to improve the performance of the application. A lot of the teams don't profile the application with Instruments at regular intervals. Here is is my method of working which I recommend. Every sprint one member of the team should be assigned a _Batman_ role in a daisy chain fashion. He is resposible for profiling the application using Time Profiler/Allocations/Leaks at the end of the sprint. If the person does not find any issues, thats fine. Whats important is that there are new set of eyes looking at the Application performance every new sprint. This not only helps keeping a tab on the performance of the application at regular intervals, but also, improves the skills and understanding of Instruments for each and every member of the team. 

