
Review processes, e.g. we had thought that a merge should need 1 core member plus 1 collaborator, unless say the review extends over 48 hours in which case 2 core members could force a merge.

There are also processes regarding whether an issue needs to be raised before a PR is submitted

We also have to manage documentation regarding SDLC for PA-DSS/PCI purposes, which may at times change the review/PR process, especially where this relates to changes to code that affect code security or code that manages credit card PAN's etc.



Some other recommendations: Require Unit Tests be written as part of a PR for all non trivial changes, Require PHPDOCs be added (for updated functions, methods, and classes), and encourage a comment per every 10 or so lines of code.

I know many programmers dislike writing Unit Tests... But writing good Unit Tests not only helps avoid bugs, but also encourages thinking about what problems may come up during runtime and how others may try to use the code.
