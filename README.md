# makefile_hacking
Hacking around with makefiles for fun and no profit

## Introduction
If there's one thing I don't like about a lot of software, it's the existance of "special features". I'm sure there's a better word for the pattern I'm talking about, but what I mean are little bits of "syntactic sugar" which break the conventions established by the rest of the system to provide some extra functionality. These special features can act as a shorthand for common operations (ex. ), as a

As a side note, I want to quickly bring up the kind of things I'm not talking about. The Python spread operator, C++'s preprocessor builtins (a whole other set of issues), and basically all of VIM could be argued to fall under these "special features", but to me these fall into a different box. Specifically, these tools do not subvert the standard due to their consistancy. The spread operator is not something that can be used exclusively on Lists, but on any itterable object. VIM's keybindings have become their own standard. The specific annoyances come from tools that have a single job, establish the conventions by which they're going to complete that job, and then break those conventions. What's the specific problem? Verbosity. The special features which I have a problem with are the ones that say "Hey, I've provided you a method to complete this task which anyone looking at it in the future will be able to understand. How would you like to force them to dig into the man pages for an hour to save 3 keystrokes?"

I'm going to be taking a deep dive into make and makefiles. A lot of people will tell you it's unnecessary to learn make since for the most part we've moved on to other build systems, or in the case of C/C++, tools that create the makefiles for us. This is true. Use those tools. Makefiles are brittle, overly verbose, and are still too high level to gain a significant level of control over your code. However, make is a standard. There's basically a 100% chance that you can find make in your package manager or build it from source on any machine in your house. Due to its ubiquity, you're going to run into makefiles at some point, and should be able to read and understand them. Unfortunately, this means learning a lot of those little "special features" which make developers so proud of themselves. I'm going to be starting off with the basics of make and makefiles, digging into the conventions of make, then we'll cover the special features which break these conventions, and finally, we'll abuse the hell out of make.

So what does Make do? Well, it's primary job is to run commands
    1. When necessary
    2. When all prerequisites for the commands are met
    3. When running commands would produce a prerequisite for the desired command

Make operates on a model of rules. A rule is made up of a Target (or multiple targets, but don't do this if you can avoid it), and Prerequisites.
Ex.
Target: Prereq1 Prereq2 Prereq3
    <Command 1>

Read this rule as: Produce Target by running <Command 1> as long as Prereq1, Prereq2 and Prereq3 exist.

So what happens if one of these Prereqs doesn't exist? That produces the dreaded "
