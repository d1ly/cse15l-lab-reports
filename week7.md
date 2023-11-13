# CSE15L Week 7 Lab Report - Vim

## Step 4. Log into ieng6
Keys pressed: `<up>, <enter>`
From my local terminal was my `ssh cs15lfa23nr@ieng6.ucsd.edu` command, and it was my last used command,
so i pressed `<up>` to easily access it.
![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/b7676383-d70b-42d8-9c25-cd598a722157)

## Clone your fork of the repository from your Github account
Keys pressed: `git clone, <ctrl+v>, <enter>`, assuming the github link is already copied

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/de76a595-9cf7-45f6-998d-dcbf37fd1e61)

## Run the tests, demonstrating that they fail
Keys pressed: `cd l, <tab>, <enter>, bash t, <tab>, <enter>`

I type in `cd l` and then `<tab>` so that it autocompletes to `cd lab7/`, so I am able to change directories quickly. The same applies to `bash t` so that it
autocompletes to `bash test.sh` to run the tests quickly.
![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/ab3f9bb8-ae1e-4c06-9d69-92b4f9c7fba1)


## Edit the code file to fix the failing test
Keys pressed: `vim <shift>L, <tab>, .j, <tab>, <enter>`

I type `vim` to start the command to edit the file. Then `<shift> + L` is the first character of "ListExamples" and we autocomplete using `<tab>`. Since there are multiple files with the name in the directory (ex. ListExamples.class  ListExamples.java  ListExamplesTests.class  ListExamplesTests.java), it doesn't autocomplete the full filename extension as it is unsure of which file. Also it likely autocompletes in alphabetical order so it will tab "ListExamples" first before "ListExamplesTest". Then I type in `,j <tab>` to autocomplete so that it accesses the `.java` ListExamples file and not the `.class` file.

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/cbf93b5a-9463-468d-81eb-ffa70ea54686)

Assuming that, when I use `vim` it opens at the very beginning of the file,

Keys pressed: `<shift> + <down>, <down>, e, r, 2, :wq, <enter>`

`<Shift>+<down>` let me skip all the way down to the comment line `// change index1 below to index2 to fix test`.

I press `<down>` to access the line below, `index1 += 1`.

Then I press `e` to skip to the end of the word (the last letter of the selected word, `index1`).

Then I press `r`, which means replace, to enter replace mode at the current highlighted character.

Pressing `2` replaces the `1` char with `2`, successfully changing `index1` to `index2`.

Pressing `:wq` is a command to save and quit the file, and `<enter>` to execute it.

Below is what `vim` looks like after I changed `index1` to `index2` and before I pressed `:wq`
![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/7364ddd3-cba9-4173-b717-33c8c3c09470)


## Run the tests, demonstrating that they now succeed

Keys pressed: <up>, <up>, <enter>

The `bash test.sh` command is up two commands in the bash history, so i pressed `<up>` two times to access it. This successfully reruns the tests.

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/4ddd5363-720e-4607-947f-aadc58d96a07)

## Commit and push the resulting change to your Github account (you can pick any commit message!)

Keys pressed: `git add L, <tab>, <enter>,
git com, <tab>, <enter>,
i, Fixed merge function ,<esc>, :wq,
git push`

![image](https://github.com/d1ly/cse15l-lab-reports/assets/146896640/c293ead8-95cc-4a18-abb3-2f10b8a63f30)

