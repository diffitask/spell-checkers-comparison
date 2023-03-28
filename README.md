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

The **most important** metric is the **percent of invalid words in the text after spell checker work**, because the main
user's
desire is to get as correct text as possible at the output. So the spell checking tools were sorted in the descending
order of
this metric.

Hunspell wins!)

## Analyzed tools overview

### Tool 1

### Tool 2

### Tool 3

## Conclusion