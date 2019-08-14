# Border Crossing Analysis

## Table of Contents
1. [Problem](README.md#problem)
1. [Steps to submit your solution](README.md#steps-to-submit-your-solution)
1. [Input Dataset](README.md#input-dataset)
1. [Expected output](README.md#expected-output)
1. [Instructions](README.md#instructions)
1. [Tips on getting an interview](README.md#tips-on-getting-an-interview)
1. [Questions?](README.md#questions?)

## Problem
The Bureau of Transportation Statistics regularly makes available data on the number of vehicles, equipment, passengers and pedestrians crossing into the United States by land.

**For this challenge, we want to you to calculate the total number of times vehicles, equipment, passengers and pedestrians cross the U.S.-Canadian and U.S.-Mexican borders each month. We also want to know the running monthly average of total number of crossings for that type of crossing and border.**

## Steps to submit your solution
* To submit your entry please use the link you received in your coding challenge invite email
* You will only be able to submit through the link one time
* Do NOT attach a file - we will not admit solutions which are attached files
* Do NOT send your solution over an email - We are unable to accept coding challenges that way
* For a limited time we have made available a <a href="http://ec2-3-225-56-40.compute-1.amazonaws.com/test-my-repo-link">website</a> that will allow you to simulate the environment in which we will test your code. 

### Creating private repositories
To avoid plagiarism and any wrongdoing, we request you to submit a private repository of your code. Both GitHub and Bitbucket offer free unlimited private repositories at no extra cost.
* Create a private repository on GitHub or Bitbucket with the given repository structure. Here is how you will be sharing your private repositories for us to see once you are ready to submit.
* Add "insight-cc-bot" as a collaborator in your project.
  * [How to add collaborators on GitHub?](https://help.github.com/articles/inviting-collaborators-to-a-personal-repository/)
  * [How to add users and groups as collaborators in Bitbucket?](https://confluence.atlassian.com/bitbucket/grant-repository-access-to-users-and-groups-221449716.html)
* **We will NOT be grading submissions we do not have access to.**

### Submitting a link to your repository
* Use the submission box to enter the link to your GitHub or Bitbucket repo ONLY
* Link to the specific repo for this project, not your general profile
* Put any comments in the README inside your project repo, not in the submission box

## Input Dataset

For this challenge, you will be given an input file, `Border_Crossing_Entry_Data.csv`, that will reside in the top-most `input` directory of your repository.

The file contains data of the form:

```
Port Name,State,Port Code,Border,Date,Measure,Value,Location
Derby Line,Vermont,209,US-Canada Border,03/01/2019 12:00:00 AM,Truck Containers Full,6483,POINT (-72.09944 45.005)
Norton,Vermont,211,US-Canada Border,03/01/2019 12:00:00 AM,Trains,19,POINT (-71.79528000000002 45.01)
Calexico,California,2503,US-Mexico Border,03/01/2019 12:00:00 AM,Pedestrians,346158,POINT (-115.49806000000001 32.67889)
Hidalgo,Texas,2305,US-Mexico Border,02/01/2019 12:00:00 AM,Pedestrians,156891,POINT (-98.26278 26.1)
Frontier,Washington,3020,US-Canada Border,02/01/2019 12:00:00 AM,Truck Containers Empty,1319,POINT (-117.78134000000001 48.910160000000005)
Presidio,Texas,2403,US-Mexico Border,02/01/2019 12:00:00 AM,Pedestrians,15272,POINT (-104.37167 29.56056)
Eagle Pass,Texas,2303,US-Mexico Border,01/01/2019 12:00:00 AM,Pedestrians,56810,POINT (-100.49917 28.70889)
```
See the [notes from the Bureau of Transportation Statistics](https://data.transportation.gov/Research-and-Statistics/Border-Crossing-Entry-Data/keg4-3bc2) for more information on each field.

For the purposes of this challenge, you'll want to pay attention to the following fields:
* `Border`: Designates what border was crossed
* `Date`: Timestamp indicating month and year of crossing
* `Measure`: Indicates means, or type, of crossing being measured (e.g., vehicle, equipment, passenger or pedestrian)
* `Value`: Number of crossings

## Expected Output
Using the input file, you must write a program to 
* Sum the total number of crossings (`Value`) of each type of vehicle or equipment, or passengers or pedestrians, that crossed the border that month, regardless of what port was used. 
* Calculate the running monthly average of total crossings, rounded to the nearest whole number, for that combination of `Border` and `Measure`, or means of crossing.

Your program must write the requested output data to a file named `report.csv` in the top-most `output` directory of your repository.

For example, given the above input file, the correct output file, `report.csv` would be:

```
Border,Date,Measure,Value,Average
US-Mexico Border,03/01/2019 12:00:00 AM,Pedestrians,346158,114487
US-Canada Border,03/01/2019 12:00:00 AM,Truck Containers Full,6483,0
US-Canada Border,03/01/2019 12:00:00 AM,Trains,19,0
US-Mexico Border,02/01/2019 12:00:00 AM,Pedestrians,172163,56810
US-Canada Border,02/01/2019 12:00:00 AM,Truck Containers Empty,1319,0
US-Mexico Border,01/01/2019 12:00:00 AM,Pedestrians,56810,0

```

The lines should be sorted in descending order by 
* `Date`
* `Value` (or number of crossings)
* `Measure`
* `Border`

The column, `Average`, is for the running monthly average of total crossings for that border and means of crossing in all previous months. In this example, to calculate the `Average` for the first line (i.e., running monthly average of total pedestrians crossing the US-Mexico Border in all of the months preceding March), you'd take the average sum of total number of US-Mexico pedestrian crossings in February `156,891 + 15,272 = 172,163` and January `56,810`, and round it to the nearest whole number `round(228,973/2) = 114,487`

## Instructions

We designed this coding challenge to assess your coding skills and your understanding of computer science fundamentals. They are both prerequisites of becoming a data engineer. To solve this challenge you might pick a programing language of your choice (preferably Python, Scala, Java, or C/C++ because they are commonly used and will help us better assess you), but you are only allowed to use the default data structures that come with that programming language (you might use I/O libraries). For example, you can code in Python, but you should not use Pandas or any other external libraries (i.e., don't use Python modules that must be installed using 'pip').

***The objective here is to see if you can implement the solution using basic data structure building blocks and software engineering best practices (by writing clean, modular, and well-tested code).***


# Tips on getting an interview

## Writing clean, scalable and well-tested code

As a data engineer, it’s important that you write clean, well-documented code that scales for a large amount of data. For this reason, it’s important to ensure that your solution works well for a large number of records, rather than just the above example.

[Here](https://data.transportation.gov/api/views/keg4-3bc2/rows.csv?accessType=DOWNLOAD) you can find large datasets to test your code (see [here](https://data.transportation.gov/Research-and-Statistics/Border-Crossing-Entry-Data/keg4-3bc2) for more information on the data dictionary).

Note, we will use it to test the full functionality of your code, along with other tests.

It's also important to use software engineering best practices like unit tests, especially since data is not always clean and predictable.

Before submitting your solution you should summarize your approach and run instructions (if any) in your `README`.

You may write your solution in any mainstream programming language, such as C, C++, C#, Go, Java, Python, Ruby, or Scala. Once completed, submit a link of your Github or Bitbucket repo with your source code.

In addition to the source code, the top-most directory of your repo must include the `input` and `output` directories, and a shell script named `run.sh` that compiles and runs the program(s) that implement(s) the required features.

If your solution requires additional libraries, environments, or dependencies, you must specify these in your `README` documentation. See the figure below for the required structure of the top-most directory in your repo, or simply clone this repo.

## Repo directory structure

The directory structure for your repo should look like this:

    ├── README.md
    ├── run.sh
    ├── src
    │   └── border_analytics.py
    ├── input
    │   └── Border_Crossing_Entry_Data.csv
    ├── output
    |   └── report.csv
    ├── insight_testsuite
        └── run_tests.sh
        └── tests
            └── test_1
            |   ├── input
            |   │   └── Border_Crossing_Entry_Data.csv
            |   |__ output
            |   │   └── report.csv
            ├── your-own-test_1
                ├── input
                │   └── Border_Crossing_Entry_Data.csv
                |── output
                    └── report.csv

**Don't fork this repo** and don't use this `README` instead of your own. The content of `src` does not need to be a single file called `border_analytics.py`, which is only an example. Instead, you should include your own source files and give them expressive names.

## Testing your directory structure and output format

To make sure that your code has the correct directory structure and the format of the output files are correct, we have included a test script called `run_tests.sh` in the `insight_testsuite` folder.

The tests are stored simply as text files under the `insight_testsuite/tests` folder. Each test should have a separate folder with an `input` folder with the test `Border_Crossing_Entry_Data.csv` input file and an `output` folder with what should be the expected `report.csv` for that test.

You can run the test with the following command from within the `insight_testsuite` folder:

    insight_testsuite~$ ./run_tests.sh

On a failed test, the output of `run_tests.sh` should look like:

    [FAIL]: test_1
    [Thu Mar 30 16:28:01 PDT 2017] 0 of 1 tests passed

On success:

    [PASS]: test_1
    [Thu Mar 30 16:25:57 PDT 2017] 1 of 1 tests passed



One test has been provided as a way to check your formatting and simulate how we will be running tests when you submit your solution. We urge you to write your own additional tests. `test_1` is intended to alert you if the directory structure or the output for this test is incorrect.

Your submission must pass at least the provided test in order to pass the coding challenge.

The <a href="http://ec2-3-225-56-40.compute-1.amazonaws.com/test-my-repo-link">website</a> that we mentioned earlier could be used to test your code has been primarily tested on Python code but could be used for Java and C++ repos. Keep in mind that if you need to compile your code (e.g., javac, make), that compilation needs to happen in the `run.sh` file of your code repository. For Python programmers, you are able to use Python2 or Python3 but if you use the later, specify `python3`, which defaults to Python 3.5.2, in your `run.sh` script or `python3.7` if you use that version.

# Questions?
Email us at cc@insightdataengineering.com
