# catsoop-helper
Python scripts that I use that I use in my catsoop site development

# Install
Download the code and templates: 
```
git clone https://github.com/TonyTerrasa/catsoop-helper.git
```

You need the following installed in your Python environment (available in the `requirements.txt` file)
```
et-xmlfile==1.1.0
openpyxl==3.0.10
```

Some shortcuts I've included in my bash-aliases to make my process nicer
```
alias csh-q="python ~/projects/catsoop-helper/csh.py -q"
alias csh-mkpg="python ~/projects/catsoop-helper/csh.py -mkpg"
alias csh-ntb="python ~/projects/catsoop-helper/csh.py -ntb"
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


## Questions 

Uses the [Kahoot template](https://kahoot.com/blog/2018/08/23/import-kahoot-from-spreadsheet/). The type of catsoop question is infered from the way you specify the question: 
- __1 correct answer:__ multiple choice
- __2+ correct answers:__ multiple select
- __0 correct answers:__ short answer where each of the given options is accepted

A sample xslx file in the examples file that I've included in the [examples](examples) folder. 

For example running questions on [`sample.csv`](examples/sample.csv) gives: 
```
<question smallbox>
    csq_prompt='They ____ (to be) nice.'
    csq_soln = ['are', 'have been']
    csq_check_function = lambda sub, sol: sub.lower().strip() in sol
    csq_size = 30 # width of text box
    csq_explanation = 'Both the present simple and present perfect are acceptable tenses in this case.'
</question>

<question multiplechoice>
    csq_renderer = 'radio'
    csq_prompt='The ________ singer of Paramore is Hayley Williams.'
    csq_options= ['principal', 'amazing', 'lead', 'chart']
    csq_soln = 'lead'

</question>

<question multiplechoice>
    csq_renderer = 'checkbox'
    csq_prompt='101 cm is _______  as big as 102 cm. (Check all that apply)'
    csq_options= ['almost', 'barely', 'very', 'not quite']
    csq_soln = [True, False, False, True]

</question> 

```

## Number Text Blanks
This is helpful if you have a text and you want to turn it into a fill-in-the-blank exercise. For example, give something like the the following ([`number-me.md`](examples/number-me.md))
```
For each bolded word, fill in a new word according to the symbol:
* (===) synonym 
* (-->) related word
* (<->) opposite

Much like many of my __(=== class)__ at university, the goal of this website is to __(<-> take away)__ students with __(--> explain)__ and novel ways to explore the content, in this case English.
```

It will number the three blanks given in between __([text])__ like this: 

```
For each bolded word, fill in a new word according to the symbol:
* (===) synonym 
* (-->) related word
* (<->) opposite

Much like many of my __(1, === class)__ at university, the goal of this website is to __(2, <-> take away)__ students with __(3, --> explain)__ and novel ways to explore the content, in this case English.
```
