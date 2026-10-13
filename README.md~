# Google's Python Class exercises

This folder contains the exercises downloaded from [Google's Python Class](https://developers.google.com/edu/python), a free course created by Nick Parlante at Google. The course combines written lessons, videos and exercises, progressing from strings and lists to files, regular expressions and external programs.

## How to use this repository

Install Python 3, then obtain a local copy using either option below.

### Download as a ZIP file

Open [this repository on GitHub](https://github.com/BjornFJohansson/google-python-exercises) and click the green ![Green GitHub Code button](images/github-code-button.png) button above the file list, shown below:



In the menu that opens, click **Download ZIP**. Extract the downloaded archive, then open a terminal in the extracted folder containing `hello.py` and `README.md`.

### Clone with Git

If Git is installed, run:

```bash
git clone https://github.com/BjornFJohansson/google-python-exercises.git
cd google-python-exercises
```

With either method, check your Python installation from that folder:

```bash
python3 hello.py
```

On Windows, use `python` instead of `python3` if that is the name of your Python executable. Open the exercise files in your editor, complete their placeholders, and run them from the terminal. For example:

```bash
python3 basic/string1.py
```

## Suggested exercise order

Follow the progression in [Google's Python Class](https://developers.google.com/edu/python): setup and introduction, strings, lists and sorting, dictionaries and files, regular expressions, then utilities and HTTP. The [Basic Python Exercises page](https://developers.google.com/edu/python/exercises/basic) groups the first exercises as strings, lists and word counting, with additional practice in `string2.py`, `list2.py` and `mimic.py`. The sequence below places that extra practice immediately after its main exercise.

| Order | File to complete | Problems and skills |
| --- | --- | --- |
| 1 | `hello.py` | Run the supplied program to check your Python setup; try passing your name as a command-line argument. |
| 2 | `basic/string1.py` | Implement `donuts` (format a count, using “many” for 10 or more), `both_ends` (combine the first and last two characters), `fix_start` (replace later occurrences of the first character with `*`) and `mix_up` (swap the first two characters of two strings). |
| 3 | `basic/string2.py` — additional practice | Implement `verbing` (apply the specified `ing`/`ly` suffix rules), `not_bad` (replace a `not`…`bad` span with `good`) and `front_back` (combine the front halves, then the back halves, of two strings; give the front half the extra character for odd lengths). |
| 4 | `basic/list1.py` | Implement `match_ends` (count strings of length at least two with matching first and last characters), `front_x` (sort strings with those beginning with `x` first) and `sort_last` (sort tuples by their final element). |
| 5 | `basic/list2.py` — additional practice | Implement `remove_adjacent` (collapse consecutive duplicates) and `linear_merge` (merge two sorted lists into one sorted list, aiming for linear time). |
| 6 | `basic/wordcount.py` | Read a text file and count words without distinguishing uppercase from lowercase. Implement `--count` to print counts in alphabetical order and `--topcount` to print the 20 most frequent words. Use `small.txt` first, then `alice.txt`. |
| 7 | `basic/mimic.py` — optional extra | Build a dictionary mapping each word to the words that follow it, retaining repetitions. Generate 200 words by choosing successors randomly, using the empty-string entry to start and as a fallback. |
| 8 | `babynames/babynames.py` | Extract the year and name/rank pairs from the supplied HTML using regular expressions. Return the year followed by names and ranks in alphabetical order; print summaries, then add `--summaryfile` to save them. See [Baby Names](https://developers.google.com/edu/python/exercises/baby-names). |
| 9 | `copyspecial/copyspecial.py` | Find filenames containing double underscores around one or more word characters, such as `xyz__hello__.txt`. First list their absolute paths, then implement `--todir` copying and `--tozip` archiving with an external program. See [Copy Special](https://developers.google.com/edu/python/exercises/copy-special). |
| 10 | `logpuzzle/logpuzzle.py` | Extract unique puzzle-image URLs from the supplied logs and sort them. Download the slices and create an HTML page to display them together; extend the sorting rule to reconstruct the second puzzle. See [Log Puzzle](https://developers.google.com/edu/python/exercises/log-puzzle). |

Complete the functions in their order within each file. For the four string/list scripts, run the provided tests after each function; `OK` means the result matches and `X` means it differs. For the larger programs, build and check one feature at a time.

Each exercise folder includes a `solution/` directory for comparison. Work in the student scripts, where the placeholders are intended for you to complete.

## Local change: ZIP paths containing spaces

On 13 October 2026, `zip_to()` in `copyspecial/solution/copyspecial.py` was changed to support spaces in both source paths and the destination archive path.

Previously, the function joined the paths into one shell command:

```python
cmd = 'zip -j ' + zipfile + ' ' + ' '.join(paths)
(status, output) = subprocess.getstatusoutput(cmd)
```

The paths were not quoted. A directory such as `Mestrado em Biologia Computacional Molecular e Ambiental` was therefore split into several command arguments. The `zip` program could not locate the input files and reported “Nothing to do!”. This is a path-handling bug, independent of the Python version.

The implementation now passes each argument separately:

```python
cmd = ['zip', '-j', zipfile, *paths]
result = subprocess.run(cmd, capture_output=True, text=True)
status = result.returncode
output = result.stdout + result.stderr
```

`subprocess.run()` uses no shell by default, so spaces within each path are preserved. The exercise still calls the external `zip` program with `-j`, which stores filenames without their directory paths. It prints the arguments before running the command and retains the existing error handling: a nonzero ZIP exit status causes the script to print the captured output to standard error and exit with status 1.

The external `zip` executable must be installed and available on `PATH`.

From this folder, an example command is:

```bash
python3 copyspecial/solution/copyspecial.py --tozip "/tmp/special files.zip" copyspecial
```

The quotes in this terminal command ensure that the shell passes the archive path to Python as one argument. Inside Python, the argument list preserves each path when invoking `zip`.

## Verification

The fix was tested with Python 3.15.0 using source paths and a destination archive path containing spaces. ZIP creation succeeded, and the archived filenames and file contents were checked against the source files.

The downloaded exercises were also checked with Python 3.15.0: all 19 Python files compiled and imported, all 41 supplied basic solution tests passed, and the Baby Names solution ran on all 10 supplied HTML datasets. Word counting, mimic generation, log URL extraction and special-file copying also ran successfully. Remote image downloads were not tested.

Only the ZIP solution was modified in this downloaded copy. Student exercise placeholders remain available for learners to complete.

## Attribution and license

The original exercise code is credited to Nick Parlante at Google Inc. See `NOTICE.txt` for attribution and `LICENSE.txt` for the Apache License, Version 2.0 supplied with the code.
