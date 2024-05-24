This is the simplest makefile that can produce the dreaded
    "make: *** No rule to make target '[Prerequisite]', needed by '[Target]'.  Stop."
error.

Fortunately, this error tells us exactly what is going on. It tried to create [Target] by running the only rule in the file, but found that [Prerequisite] was needed. [Prerequisite] is going to be a file somewhere adjacent to or above the Makefile itself. If Make can't find the [Prerequisite] file, then it starts to look into the other rules in the Makefile. "Maybe one of these other rules creates [Prerequisite], and then I can create [Target] once I have it!". In the case of this error, [Prerequisite] was not found in the folder with Make, and there is no rule to generate it, hence the error.
