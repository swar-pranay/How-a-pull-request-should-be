# How-a-pull-request-should-be
Basic checkpoints before submitting a pull request/ merge request.

These are some of the check points that we follow in the company where I work. These checkpoints are not for the reviewer per se but more for the person submitting the Pull/Merge request to have list to go through before finally raising the flag for 'ready for peer review' after submitting the Pull/ Merge request. 

[x] Does the code compile for all relevant targets.
I know this sounds rather obvious, but there are times when we would make this one line change or even one character change for may be a defect fix and don't really compile and check since the results are obvious.

[x] Does the code compile cleanly without warnings/errors. 
This is to make sure that your changes did not add any new warnings to the code. By warnings/errors, I mean two types a) those given by the compiler. b) The warning/errors given by any other linting program that you could be using in your software development peocess. We use SwiftLint for Swift source code. This also makes sure the entire code base is in aggrement with the set standards for styling and convention.


