# Tom's super cool PF style tips

_An appendix to my [[Courses/Year 1/Semester 1a/Programming Fundamentals]] page_

Are you mad at getting deducted all the time by the TA's for something you completely missed when you were reviewing your code for your final submission? Well, look no further! This page contains nearly every style-related trick/config I've found over the past 5 weeks...

We will be installing the `clangd` extension for VSCode (it's better than the official extension for C/C++ anyways), so we can load Tom's super cool configuration files that prevent Rookie Mistakes<sup>(TM)</sup>

This includes:
- Automatic indentation and brace placement
- Tidy formatting in general
- Following identifier casing convention
- Warns on short identifier names
- Warns on too many or too few parentheses
- Warns when you miss a brace around a single-statement `if` or `while`

AFAICT (though of course you can't hold me accountable if I'm wrong) this *should* catch most cases where you can get deducted. Two notable exceptions are **commenting** and **memory management**. The latter will see a nifty bonus trick at the end of this page.

![[Courses/Year 1/Semester 1a/Programming Fundamentals/a52b05e5-4c12-4ea5-9666-825be3688ff6.png]]

## Prerequisites

Download clangd for VSCode: https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd (you should be able to install it from the link, or just search for it inside VSCode itself)

Also, we want the *Format on save* setting to be turned on, so you don't have to manually format every time. It looks like this:

![[Courses/Year 1/Semester 1a/Programming Fundamentals/6dfd5827-2ee7-4e6a-ac7f-636530ac6764.png]]

Direct link: <vscode://settings/editor.formatOnSave>

**NB**: VSCode might give you two pop-ups:

![[Courses/Year 1/Semester 1a/Programming Fundamentals/f3d4a4b0-b6bc-44e0-b027-fa691817e986.png]]

Respond respectively with **Disable IntelliSense** and **Install** to make sure that clangd will work properly.

## Loading the configuration files

Now, download and unzip the [styleshizzle](https://fs.toostveen.nl/pub/UG/CS-1/prog-fund/styleshizzle?zip) in your PF-lab project folder. It should look like this:

![[Courses/Year 1/Semester 1a/Programming Fundamentals/c83c3b5c-d2ce-471f-a2cb-cc2fa4607711.png]]

## Checking that it works

Copy the following code in your editor now, and watch the formatter kick in, and the warnings showing up:

```c
#include <stdio.h>

#define snake_case_macro 1 
#define camelCaseMacro 1 
#define AjAsj 2

void SNAKE_CASE(void) {}

// note the brace below is wrong
int main(int argc, char **argv)
{
    int SNAKE_CASE_LOCAL = 1;
  int snake_case_local = 1;
    int CamelCaseLocal = 1;

     int a = 1; int b = 2;

    if (a == 1) printf("");

    int c = a + b * b;

    if (c == c) {
if (c == c) {
        if (c == c) {
            while (c == c) {
            }}
        }
    }
}
```

Obviously, after formatting, you'll still get errors:
![[Courses/Year 1/Semester 1a/Programming Fundamentals/db36edb7-1ad4-4388-99c4-7c1ff79180d5.png]]

# Bonus: memory management diagnostics

Have you ever found yourselves in one of the following situations?:
- `Segmentation fault (core dumped)`
- Memory leaks / deducted for missing `free()`
- Off-by-ones that do not crash but silently lead to wrong answer

Boy, do I have a compiler flag for you! Next time, compile with:

```bash
gcc -std=c99 -Wall -pedantic -fsanitize=address -ggdb myThing.c
```

**WARNING**: using this compiler flag may terminate the program early, and so it will not reflect the program's actual behaviour when submitted to Themis. When testing, always compile with the same command as specified by Themis to prevent any subtleties messing with the final judgement.

This modifies the final binary so that the "address sanitizer" (ASan for short) tracks any memory allocations/accesses the program makes. If your program "messes up", ASan will crash the program immediately and tell you what is up:

![[Courses/Year 1/Semester 1a/Programming Fundamentals/f6e73a84-6269-4214-b26a-19bee63cf028.png]]

Hey, a memory leak! You can see the program did its job fine, but after that ASan found that these two arrays never got freed, and it also knows they were allocated at lines 82 and 83 in `bernoulli2.c`. Let's look at those lines:

![[Courses/Year 1/Semester 1a/Programming Fundamentals/a5b77bfd-16c5-4cda-9ed9-3b702dcdc131.png]]

**AHA**! I guess I forgot to free `prev` and `cur`...

ASan detects and diagnoses all sorts of these memory-management bugs. Use it to your advantage.

Notable mention: there's also *valgrind* but for our current purposes that's like using a nuclear missile to kill an ant...