# Spell checkers comparison

## General description

This research presents an exploration of some popular existing spell checkers and the evaluation of their work.

6 tools were selected for the analysis:

* [Pyspellchecker library](https://github.com/barrust/pyspellchecker)
* Textblob library
* Pre-trained model from [Spello](https://pypi.org/project/spello/) library
* [Hunspell](https://github.com/hunspell/hunspell) spelling corrector
* [Jamspell](https://github.com/bakwc/JamSpell) spelling corrector
* [Autocorrect](https://github.com/filyp/autocorrect) library

Each tool was tested on a text, created using the dataset of correct words and their misspelled
forms. [Dataset](https://www.kaggle.com/datasets/bittlingmayer/spelling?resource=download&select=wikipedia.txt) was
collected by Wikipedia editors.

To evaluate the tools, the following metrics were used:

* Classifying recall
* Classifying precision
* Classifying accuracy
* Percent of words that are invalid after checker work
* Percent of the misspelled words, that were correctly fixed by spellchecker
* Percent of non-fixed misspelled words, but for which the right decision was in top-5 spellchecker correction
  suggesting
* Percent of originally correct spelled words that were broken by the checker

## Table of Contents

## Spell checking tools selection

During the search, such useful and popular tools for spell correction were also found and could be tested in future
researches:

* [Contextual spell check library](https://pypi.org/project/contextualSpellCheck/)
* [Grammarly API](https://developer.grammarly.com/)
* [Yandex speller API](https://yandex.ru/dev/speller/)
* [PySpelling plugin](https://facelessuser.github.io/pyspelling/api/)
* [DeepSpell model](https://github.com/MajorTal/DeepSpell)

## Dataset and metrics

A detailed description of the datasets and the selected metrics is written in
the [notebook](https://github.com/diffitask/spell-checkers-comparison/blob/main/spell-checkers-comparison.ipynb). Also,
here you can find the code of how the analyzed spell checking tools work on test data and measurements of metrics for
each checker.

## Benchmarks

<table>
  <tr>
    <td></td>
    <td><b>Invalids after checker</b></td>
    <td><b>Accuracy</b></td>
    <td><b>Speed<br>
(words/sec)</b></td>
    <td>Recall</td>
    <td>Precision</td>
    <td>Fixed</td>
    <td>Non-fixed with correction in top-5</td>
    <td>Broken</td>
  </tr>
  <tr>
    <td>Hunspell</td>
    <td>15.01%</td>
    <td>97.78%</td>
    <td>58</td>
    <td>98.78%</td>
    <td>97.31%</td>
    <td>75.97%</td>
    <td>67.74%</td>
    <td>3.49%</td>
  </tr>
  <tr>
    <td>Jamspell</td>
    <td>21.77%</td>
    <td>90.29%</td>
    <td>284</td>
    <td>86.51%</td>
    <td>95.76%</td>
    <td>65.01%</td>
    <td>56.65%</td>
    <td>4.89%</td>
  </tr>
  <tr>
    <td>Pyspellchecker</td>
    <td>22.12%</td>
    <td>97.10%</td>
    <td>32</td>
    <td>98.70%</td>
    <td>96.22%</td>
    <td>64.44%</td>
    <td>56.26%</td>
    <td>4.94%</td>
  </tr>
  <tr>
    <td>Spello</td>
    <td>22.34%</td>
    <td>92.80%</td>
    <td>1013</td>
    <td>96.90%</td>
    <td>90.86%</td>
    <td>69.90%</td>
    <td>47.05%</td>
    <td>12.43%</td>
  </tr>
  <tr>
    <td>Autocorrect</td>
    <td>23.60%</td>
    <td>92.23%</td>
    <td>38</td>
    <td>93.07%</td>
    <td>93.07%</td>
    <td>64.85%</td>
    <td>55.57%</td>
    <td>8.84%</td>
  </tr>
  <tr>
    <td>Textblob</td>
    <td>28.03%</td>
    <td>86.79%</td>
    <td>10</td>
    <td>88.06%</td>
    <td>88.34%</td>
    <td>61.63%</td>
    <td>37.87%</td>
    <td>14.83%</td>
  </tr>
</table>

## Results interpreting

### Gradation of metrics importance

The **most important** metric is the **percent of invalid words in the text after spell checker work**, because the main
user's
desire is to get as correct text as possible at the output. So the spell checking tools were sorted in the descending
order of
this metric.

Next in importance are accuracy, which shows how well the checker determines the spelling of a word in general, and the
speed of the checker, which indicates how long the user will have to wait.

The other metrics are interesting but less important.

### Spell checking tools overview

#### Hunspell

Hunspell wins!) It has medium speed, but the highest accuracy and the lowest errors number in the output text. One of
the reasons, why this tool is so good (and popular) -- in addition to having a large vocabulary, Hunspell also knows a
lot of extreme cases and explicitly flags some existing or forbidden words, which improves the accuracy of his word
classification ([article](https://zverok.space/blog/2021-03-16-spellchecking-dictionaries.html)). Another Hunspell
benefit, that doesn't test in this research, is that its special format dictionaries are available for more than 100
languages.

#### Jamspell

Jamspell competed with Hunspell a few years ago, and, as its creators wrote in 2020, it showed even better results.
Although it still works 5 times faster than the Hunspell, but as we can see, in our testing Jamspell performed worse
results and left 6% more errors in the final text. Classifying accuracy of Jamspell is also lower than Hunspell
accuracy -- by 7%.

Jamspell is written in C++ -- the fastest language -- in particular, this is why he has such a high speed of work. But
it should have learned how to fix words better.

#### Pyspellchecker

Spell checking [library](https://github.com/barrust/pyspellchecker) that
implements [Peter Norvig's](https://norvig.com/spell-correct.html) algorithm idea, which many subsequently turned to for
comparison or improvement.

*How does it work?*

Clipping from the library description:
"It uses a [Levenshtein Distance](https://en.wikipedia.org/wiki/Levenshtein_distance) algorithm to find permutations
within an edit distance of 2 from the original word. It then compares all permutations (insertions, deletions,
replacements, and transpositions) to known words in a word frequency list. Those words that are found more often in the
frequency list are more likely the correct results."

*Strengths and weaknesses*

Because of many permutations calculating it doesn't work fast, but on the other hand, it classifies words very
accurately as correct or non-correct (classifying accuracy is almost the same as in the Hunspell case), but it does not
correct words so well.

#### Spello

The fastest library! It looks very cool, even though a small model for English was used in this research. Perhaps the
larger model works even more efficiently! (but it should be tested first).

#### Autocorrect

Autocorrect library also based on Peter Norvig's spelling corrector. Not very fast, but 4 times faster than Textblob
library and even faster than the Pyspellchecker. In general, the results are slightly worse than the Pyspellchecker. As
a benefit, it's can be noted that the library supports more than 12 languages and makes it easy to add new languages.

#### Textblob

The lowest and the worst library in our analyzed tool set... also based on Peter Norvig's article and calculates
Levenshtein distances (that's why it's so slow). It makes user to wait for a long time and the output text
is almost 1/3 made up of errors. In the Internet I found some examples of using this tool together with Pyspellchecker:
first, the Pyspellchecker library detects misspelled words, and then the Textblob works purely as a misspellings
corrector. Maybe this combination could give better results.

## Conclusion

If accuracy is important in your task and the very high speed is not necessary, it is better to use Hunspell. If there
is some application where speed is critical and the output text could have some spelling errors, maybe your way is to
use Spello.