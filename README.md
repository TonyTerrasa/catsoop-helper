# catsoop-helper
Python scripts that I use that I use in my catsoop site development

# Install
Download the code and templates: 
```
$ git clone https://github.com/TonyTerrasa/catsoop-helper.git
```

You need the following installed in your Python environment
```
@@include[requirements.txt](requirements.txt)
```

Some shortcuts I've included in my bash-aliases to make my process nicer
```
@@include[requirements.txt](requirements.txt)
```

# Usage
```
usage: csh.py [-h] [-q QUESTION] [-mkpg MKPG [MKPG ...]]
              [-ntb NUMBER_TEXT_BLANKS]

options:
  -h, --help            show this help message and exit
  -q QUESTION, --question QUESTION
                        Create catsoop style questions from the input .xslx or
                        .csv file. Format based on the excel template for
                        making Kahoot questions
  -mkpg MKPG [MKPG ...]
                        Create a new directory for a new catsoop page. First
                        argument is taken as the directory name. Second
                        (optional) argument is the name for the preload.py.
  -ntb NUMBER_TEXT_BLANKS, --number-text-blanks NUMBER_TEXT_BLANKS
                        Numbers the blanks in a text with the format
                        __([text])__. Give a readable text file.
```
