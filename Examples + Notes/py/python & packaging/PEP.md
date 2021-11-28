Python Enhancement Proposals(PEP) are suggestions for improvements to the language, made by experienced Python developers.

**PEP 8** is a style guide on the subject of writing readable code. It contains a number of guidelines in reference to variable names, which are summarized:

-   modules should have short, all-lowercase names;
-   class names should be in the CapWords style;
-   most variables and function names should be lowercase\_with\_underscores;
-   constants(variables that never change value) should be CAPS\_WITH\_UNDERSCORES;
-   names that would class with Python keywords should have a trailing underscore.

**PEP 8** also recommends using spaces around operators and after commas to increase readability.

note: however, whitespace shouldn't be overused. For instance, avoid having any space directly inside any type of brackets.

Other **PEP 8** suggestions include the following:

-   lines shouldn't be longer than 80 characters;
-   'from module import \*' should be avoided;
-   there should only be one statement per line.

It also suggests that you use spaces, rather than tabs, to indent. However, to some extent, this is a matter of personal preference. If you use spaces, only use 4 per line. It's more important to choose one and stick to it.

The most important advice in PEP is to ignore it when it makes sense to do so. Don't bother with following PEP suggestions when it would cause the code to be less readable, inconsistent with the surrounding code, or not backwards compatible.

however, by and large, following PEP 8 will greatly enhance the quality of the code.

Some other notable PEPs that cover code style:

**PEP 20**: the Zen of Python

**PEP 257**: Style Conventions for Docstrings