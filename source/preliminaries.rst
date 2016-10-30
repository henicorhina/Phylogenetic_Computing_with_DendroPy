*************************************
Preliminaries: Before Getting Started
*************************************

For the at least the duration of this tutorial (or, if you get bitten by the bioinformatics/programming bug, maybe the rest of your life), you are going to be "living" primarily in two environments: the shell (a.k.a., colloquially, as the "the command line" or "Terminal") and the text editor.
Getting comfortable with both are a priority before proceeding.
This chapter will go over what you need and what you need to know, as well as details on how you can go about this.

.. note::

    This entire tutorial assumes that you will be working with a POSIX shell, such as BASH, which will be the case if you are running any flavor of OSX (Mac's), Unix's, or Linux.

    If you are running Windows, on the other hand, then you have the following options:

    1. Use the stock Windows shell or PowerShell.
       You will have to adapt the shell commands (such as listing files, navigatring directories, etc.), but all the Python-specific (and DendroPy-specific) stuff will be the same.
       If your primary work environment is Windows, this is probably the best bet in the long run.
       But if you are not already comfortable with working with the Windows shell, you probably want to work on this before going any further, so that it does not distract you from learning DendroPy.
       `This site <http://www.digitalcitizen.life/command-prompt-how-use-basic-commands>`_ gives an overview of the commands and conventions that you would want to target for learning.

    2.  If you are running Windows 7 or 8, and are not comfortable enough with the Windows shell and PowerShell to "translate" the shell commands as you follow along, then your best bet is to install Cygwin, which is available here:

            https://www.cygwin.com/

        and spend some time in getting familiar in launching or otherwise using it.

    3.  If you are running Windows 10, you can also install Cygwin, but, you might actually prefer installing a full-fledged BASH shell by following these instructions:

            http://www.howtogeek.com/249966/how-to-install-and-use-the-linux-bash-shell-on-windows-10/


What You Need To Have
=====================

You need to make sure that, on your machine, you have installed:

-   Python 2.7 or greater.
-   A *good* text editor.


Python Installation
-------------------

You need to have either Python 2.7, Python 2.8, or Python 3 (any sub-version) installed on your machine. You can check to see what Python you have by opening a shell session (see below) and typing::

    $ python --version

at the prompt. You should see something like::

    Python 2.7.10

Typically, the default system Python will be major version in the 2 series.

You can check to see if you have Python 3 running by typing::

    $ python3 --version

If you get a response like::

    -bash: python3: command not found

then you do not have Python 3 installed.
Otherwise, you should get a response like::

    Python 3.5.0

As long as you have a Python version of at least 2.7 or greater, you are doing fine.
If you happen to have both Python 2.7 and some version of Python 3 installed, it is up to you which you choose to use (see note below).
If you happen to *not* have a Python version of 2.7 or greater, you should go to http://python.org and download an install the latest version in either the 2.x series or 3.x series (again, see note below as to choosing between 2 and 3).
You might be running a Python under one of the

.. note::

    DendroPy runs equally well under both Python 2 (2.7 and greater) and Python 3 (all versions). We

Text Editor
-----------

A *good* general-purpose text-editor is an important tool to know and to know well.
For many applications in life and in work, it will be your most-used and most-reliable tool in your arsenal.
Choose a good general-purpose text-editor now, and learn it, and learn it well.

The following are emphatically *not* general-purpose text editors, good or otherwise:

    -   Microsoft Office/Word, LibreOffice, OpenOffice, Pages, etc.
    -   TextEdit (Macs)
    -   NotePad (Windows)
    -   RStudio
    -   PAUP*

The following, on the other hand, *are* examples of good general-purpose text editors:

    -   Sublime Text
    -   TextWrangler
    -   NotePad++
    -   Vim
    -   Emacs
    -   BBEdit

More generally, the following are characteristics of a good general-purpose text editor:

    -   not annoying
    -   open very, very, *very* large files without complaint, while retaining performance
    -   open and view/edit multiple documents simultaneously
    -   view documents with very long lines with optional soft-wrapping
    -   comprehensive handling of different platform line-endings (e.g., opening a file with Unix/Mac/DOS line-endings without complaint or glitch and, optionally, saving the same file with a different lind-ending convention).
    -   comprehensive handling of unicode, special characters, etc.
    -   auto-expansion of the tabs to spaces, or collapsing of spaces into tabs
    -   normalization of tabs/spaces ("retabbing" or "detabbing")
    -   visualization of special characters, especially white space (tabs/spaces)
    -   support for advanced search/search-and-replace (whole word/part of word, case sensitive/insensitive, etc.)
    -   support for regular-expression based search/search-and-replace
    -   syntax coloration

For Python development, or programming/development in general, there are number of specialized IDE's (Integrated Development Environments) that work really well: KomodoIDE, WingIDE, PyCharm, XCode, etc.
You are free to use these if you prefer, but I advise against it if you are just starting out.

What You Need To Respect
========================

File and Directory Naming Conventions
-------------------------------------

    -   Stick to the 26 character standard Roman (unaccented) alphabet (``A-Za-z``), numbers (``0-9``), underscores (``\_``), periods (``.``) and/or dashes ("``-``").
    -   Use casing as you wish, but do not count on case differences to distinguish names.
    -   Do *NOT* use spaces ANYWHERE in the file/directory name.
    -   Do *NOT* use ANY other punctuation apart from the underscore, period or dash.
    -   Do *NOT* start a file or directory name with an underscore, period, or dash.
    -   Meaningful file/directory names are *good* (even if long).
    -   Meaningful filename extensions are *good*.
    -   Primary criterion: clear indication of contents *and* easy to type.

Python Scripts: Tab vs. Space Indent Conventions
------------------------------------------------

Those of you familiar with Python programming know that indentation line plays an important structural/semantic role: the leading whitespace on each line determines how that line is interpreted.
The Python specification allows this whitespace to be given by either regular spaces or tab characters, or both.
Here are what I recommend that you use on peril of eternal regret and shame and damnation:

**1. USE ANY INDENT CONVENTION YOU LIKE, BUT JUST MAKE SURE IT IS CONSISTENT: DO NOT MIX TABS AND SPACES.**

**2. BUT, REALLY, YOU SHOULD STICK TO WHAT WINNERS USE: FOUR (4) SPACES PER INDENT.**

**2. WHICH IMPLIES: NEVER USE TABS FOR INDENTS.**

**3. IF YOU _MUST_ USE TABS FOR INDENTS, STICK TO TABS AND ONLY TABS: NEVER USE SPACES FOR INDENTS ANYWHERE.**

**4. BUT, SERIOUSLY, PLEASE JUST BE A BEAUTIFUL PERSON ON THE INSIDE _AND_ OUT, AND JUST USE 4-SPACES FOR YOUR INDENTS, NOT TABS.**


What You Need to Know
=====================

Objectives
----------

-   Understand how to open a shell session on your machine.
-   Understand the basics of your filesystem and filesystem navigation, including:

    -   Concepts of a file and directory path.
    -   Concepts of relative and absolute paths.
    -   Concepts of where you "are" in the file system (i.e., the current directory), how to "go" to somewhere else (i.e., change the current directory) or refer to a file that is in another directory from the current directory.

Resources
---------

-   http://www.linuxnix.com/abslute-path-vs-relative-path-in-linuxunix/
-   https://www.digitalocean.com/community/tutorials/basic-linux-navigation-and-file-management
-   http://conqueringthecommandline.com/book/basics
-   http://www.digitalcitizen.life/command-prompt-how-use-basic-commands (Windows)

Exercises
=========

Basic Shell Fluency
-------------------

1.  Open a shell session and create a working directory for this tutorial. This can be located anywhere in the filesystem, but it should probably be an easy place to get to, and there should not be any spaces or special characters anywhere in its path.
    Examples are::

        ~/workshops/dendropy/tutorial
        ~/projects/dendropy-tutorial
        ~/Documents/DendroPy_Workshop

    For the remainder of the tutorial, we will refer to this directory as ``$DENDROPY_TUTORIAL``.
    So, for example, if you decided the tutorial directory was going to be ``~/Documents/dendropy-workshop``, then ``$DENDROPY_TUTORIAL/lesson-1a`` would refer to ``~/Documents/dendropy-workshop/lesson-1a`` on your filesystem.

2.  Create a sub-directory in ``$DENDROPY_TUTORIAL`` called: ``00-prelims01``. Create two subdirectories here, one called ``data`` and the other called ``bin``. When done, your directory tree should look like::

        +-- $DENDROPY_TUTORIAL
            |
            +-- 00-prelims01
                |
                +-- bin
                |
                +-- data

3.  Open your text editor and create a new text file in ``$DENDROPY_TUTORIAL/00-prelims01/data`` called ``hello.txt``, and save the following content to it::

        Hello, world.

4.  In your text editor, create anoter new text file in ``$DENDROPY_TUTORIAL/00-prelims01/bin``. This will be a Python script file called ``hello.py``, with the following content::

        #! /usr/bin/env python
        import sys
        if len(sys.argv) < 2:
            sys.exit("Path to data file not specified")
        data_f = open(sys.argv[1])
        data = data_f.read()
        print(data)

5.  Open a shell session and run the Python script file created above. You will need to be able to specify the paths to the both the script file and the data file.
    You can do this in a number of ways, depending on where (i.e., which working directory) you want to run the file in.
    You can go to the exercise sub-directory and run it from there, passing in the relative paths to the script and the data file by specifying their respective subdirectories::

        $ cd $DENDROPY_TUTORIAL
        $ cd 00-prelims01
        $ python bin/hello.py data/hello.txt

    Or you can go to the binary sub-directory and run it from there, indicating the path to the data file by using the parent directory tokens::

        $ cd $DENDROPY_TUTORIAL
        $ cd 00-prelims01
        $ cd bin
        $ python hello.py ../data/hello.txt

    Or some other working directory, with the paths appropriately specified.
    For the record, I think that the first convention (where the working directory is the "top" level project) directory is the most natural.
    Also note that while the examples here use ``python`` as the primary command, if you are interested in working with Python 3, in most systems today you will still need to specify ``python3`` as Python 2 is typically still the default.
