# CSE15L Week 9 Lab Report - Putting it All Together

## Part 1 Debugging Scenario

Student:

Hi! I'm working on the autograder bash script and I can not get it to work on correct versions of the `ListExamples.java` file, only ones with errors. Here is my output for when I run the script with broken code and one with all working code. It seems that calculating the grade doesn't really work and ends up giving a null score? Also there's some syntax error that only occurs when I run the corrected list methods file which is weird.

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/5e278e0e-0ea1-491c-8ebf-09932bc320db)

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/67b2b34b-46e1-492d-a49b-ba9e9755803e)

Here is my corresponding code for when I calculate the grade.

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/56d58d5f-ec22-451c-9517-e37103536338)


TA: 

It seems like you are extracting the number of tests run and the number of tests failed from the output of running the junit test file. However the "Tests run: 3,  Failures: 2" output only is there when you fail a test at some point, otherwise it will just say "OK" if all the tests passed. I suggest you check when junit outputs "OK" and make it output a full score when detected.

Student: 

Thanks I figured it out! Turns out that syntax '-' error comes from the `TOTAL` and `FAILURE` variables not being initalized since the output didn't have that "Tests run:" and "Failures:" output.

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/c25851f3-89c4-47fb-86f7-2cfc216f68dc)



## Information about setup

File structure

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/1dedc5f1-3330-4b58-9751-b86dfee8a93e)


Grading script before bug:

```
CPATH='.;lib/hamcrest-core-1.3.jar;lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'


# Draw a picture/take notes on the directory structure that's set up after
# getting to this point

# Then, add here code to compile and run, and do any post-processing of the
# tests

if [ ! -f "student-submission/ListExamples.java" ]
then
    echo "Required file not in respository, need ListExamples.java"
    echo ""
    echo "Grade: 0/3"
    exit 1
fi

cp student-submission/ListExamples.java grading-area/
cp TestListExamples.java grading-area/

javac -cp "$CPATH" grading-area/*.java 2> errors.txt

if [ $? -ne 0 ]
then
    echo "Compilation failed. Check for syntax or fomatting errors below:"
    echo ""
    cat errors.txt
    echo ""
    echo "Grade: 0/3"
    exit 1
fi

java -cp "$CPATH;grading-area" org.junit.runner.JUnitCore TestListExamples > testOutput.txt
cat testOutput.txt

TOTAL=$(grep -o "run: "[1-9] testOutput.txt | awk '{ print $2 }')
FAILURES=$(grep -o "Failures: "[1-9] testOutput.txt | awk '{ print $2 }')
SCORE=$(($TOTAL - $FAILURES))
echo ""
echo "Grade: $SCORE/$TOTAL"
```

Command:

bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-corrected

To fix this bug, after running the tests, make a variable to `grep` from the output the string "OK" to confirm that all the tests passed for a good file. Then output the grade and exit it, because the grade is already determined. Here is the fix in code:

```
CORRECT=$(grep -o "OK" testOutput.txt)
if [ $CORRECT == "OK" ]
then
    echo "Grade: 3/3"
    exit 1
fi
```




