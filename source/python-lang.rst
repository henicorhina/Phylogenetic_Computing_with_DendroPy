*******************************
The Python Programming Language
*******************************

Understanding the fundamentals of the Python programming language is essential before we begin looking at DendroPy.
DendroPy is a *programmer's* library.
You need to understand concepts such as statements, types, variables, functions, arguments, return values, and, while not object-oriented programming *per* *se*, at least classes and associated aspects (attributes, properties, etc.).
The last is especially important, as the phylogenetic data that you will be dealing with will be represented by specialized DendroPy *objects*, which are, of course, specific instantiations of classes, and the information that they represent will be accessed, manipulated, and operated on through various attributes and properties of these objects.
Note that you do *not* need to be an expert Pythonista to use DendroPy.
You do not need to even be a very good Python programmer.
But you *do* need to have the capability to solve problems using Python, even if it means that you will have to spend a couple of hours on Google or StackExchange or some other dead tree references trying to do so [1]_ [2]_.

.. [1] Confession I: I know of very few programmers, myself included, who do not rely on Google/StackExchange or otherwise the internet in general to see themselves through the day.)

.. [2] Confession II: I use Google/StackExchange or otherwise the internet in general to look up things relating not just to Python, but DendroPy; my memory is increasingly porous, and the internet is increasingly my Mnemosyne.


Have a peek ahead to the exercises at the end of this chapter. If, with ample time and unrestricted access to the internet, you are able to code up solutions to these without too much stress, then you are ready to move on to actually dealing with DendroPy.
Otherwise, then you will want to brush up on your Python.
Unfortunately, coverage of fundamentals of the Python programming language are well beyond the scope of this tutorial.
In the future, we hope to expand this chapter to provide a skeleton coverage of the concepts you would need to learn, with pointers to more detailed lessons and tutorials.
For now, here we present a very carefully selected resources from which you can learn the required Python.
Please note that you emphatically do *not* need to master all the material below.
In fact, you do not need to master any of the material.
You just need to know enough to (eventually) stumble through solutions to the above examples comfortably and without stress.

-   `A Byte of Python <https://python.swaroopch.com/>`_
-   `A Gentle Introduction to Programming Using Python <https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-189-a-gentle-introduction-to-programming-using-python-january-iap-2011/>`_
-   `Google's Python Class <https://developers.google.com/edu/python/?csw=1>`_
-   `Dive into Python 3 <http://www.diveintopython3.net/>`_
-   `Learn Python the Hard Way <https://learnpythonthehardway.org/>`_
-   `MIT's Introduction to Computer Science and Programming  <https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00-introduction-to-computer-science-and-programming-fall-2008/video-lectures/>`_
-   `An Introduction to Programming for Bioscientists: A Python-Based Primer <http://journals.plos.org/ploscompbiol/article?id=10.1371%2Fjournal.pcbi.1004867>`_

Exercises
---------

1.  Write a Python program that:

    -   Takes a path to a text file as input.
    -   The text file consists of multiple lines of English text.
    -   The program should read the contents of the file into a list, with each element of the list corresponding to a line in the original text file.

2.  Write a Python program that:

    -   Takes a path to a text file as input.
    -   The text file consists of multiple lines of English text.
    -   The program should read the contents of the file and orints out the word frequency of the text in the file, sorted from most frequent to least frequent, ignoring case.

3.  Write a Python program that:

    -   Takes a path to a text file as input.
    -   The text file consists of multiple lines of characters, A-Z or a-z.
    -   The program should read the lines in the file, and print them out again in order of decreasing similarity with the first line of the text, with similarity measured in terms of case-insensitive Hamming distances (p-distance).

4.  Write a Python program that:

    -   Takes a path to a text file as input.
    -   The text file consists of multiple lines of English text.
    -   Each text file will be processed into an object of a "``Literature``" class, which will have attributes that track the following information:

        -   "``style_source``": Source file identifier
        -   "``word_relationships``": a case-insensitive dictionary with keys consisting of strings representing each distinct word found in the source, and values being objects of a "Word" class.

    -   The "``Word``" class will maintain the following attributes:

        -   "``word``": the priming word, i.e. the string representing to the word corresponding to this object.
        -   "``next_word_frequencies``": a dictionary, in which the keys consist of words found in the source, and the values are the frequencies with which those words immediately follow the priming word in the source.

    -  The "``Word``" class will provide a method, "``next_word``", which will return a random word from the source, with probability proportional to its relative frequency of succeeding the corresponding priming word.
    -  The "``Literature``" class will provide a method, "``sample``":

        -   This method takes two optional arguments:

            -   a priming word string; if not specified, a random word is selected, with probability proportional to the relative frequency of its occurrence in the source.
            -   a sentence length: an integer specifying the number of words; if not specified, then this defaults to a random number sampled from a normal distribution with mean given by the average sentence (line) length in the source, and standard deviation given by the standard deviation of the sentence (line) lengths in the source.

        -   This method will return a string, consisting of a chain of words separated by a space:

            -   the length of the string will be given by the sentence length argument.
            -   the first word in the sentence will be the priming word string argument.
            -   each subsequent word will be a random word from the source, with probability of the word proportional to the relative frequency of it occurring after the previous word in the source; this is the word that is returned by the "``next_word``" method of the "``Word``" class object corresponding to the previous word.

    -   The program should enter a loop, prompting the user for a priming word and a sentence length. In the event that the user enters a null input for the priming word or a 0 sentence length, the loop terminates and the program exits. Otherwise the program will print the random sentences returned by the "``Literature.sample()``" method using the arguments supplied by the user. Note that case-insensitivity is maintained throughout.
