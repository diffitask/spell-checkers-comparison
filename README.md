# Spell checkers comparison

## General description

This research presents an exploration of some popular existing spell checkers and the evaluation of their work.

6 tools were selected for the analysis:

* [Pyspellchecker library](https://github.com/barrust/pyspellchecker)
* Textblob library
* Pre-trained model from [Spello](https://pypi.org/project/spello/) library
* [Hunspell](https://github.com/hunspell/hunspell) spelling corrector
* [Jamspell](https://github.com/bakwc/JamSpell) spelling corrector
* Autocorrect library

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

Another tools that can be useful for spell checking and correction:

* PySpelling (https://facelessuser.github.io/pyspelling/api/)
* DeepSpell model (https://github.com/MajorTal/DeepSpell)
* Contextual spell check https://pypi.org/project/contextualSpellCheck/
* Grammarly API
* Yandex speller API

## Dataset and metrics

A detailed description of the datasets and the selected metrics is written in
the [notebook](https://github.com/diffitask/spell-checkers-comparison/blob/main/spell-checkers-comparison.ipynb). Also,
here you can find the code of how the analyzed spell checking tools work on test data and measurements of metrics for
each checker.

## Benchmarks

<table>
  <tr>
    <td></td>
    <td>Recall</td>
    <td>Precision</td>
    <td>Accuracy</td>
    <td>Invalids after checker</td>
    <td>Fixed</td>
    <td>Non-fixed with correction in top-5</td>
    <td>Broken</td>
    <td>Speed<br>
(words/sec)</td>
  </tr>
  <tr>
    <td>Hunspell</td>
    <td>98.78%</td>
    <td>97.31%</td>
    <td>97.78%</td>
    <td>15.01%</td>
    <td>75.97%</td>
    <td>67.74%</td>
    <td>3.49%</td>
    <td>63</td>
  </tr>
  <tr>
    <td>Spello</td>
    <td>96.90%</td>
    <td>90.86%</td>
    <td>92.80%</td>
    <td>22.53%</td>
    <td>69.57%</td>
    <td>47.68%</td>
    <td>12.43%</td>
    <td>930</td>
  </tr>
  <tr>
    <td>Jamspell</td>
    <td>99.71%</td>
    <td>56.06%</td>
    <td>56.04%</td>
    <td>21.64%</td>
    <td>64.97%</td>
    <td>60.87%</td>
    <td>4.53%</td>
    <td>365</td>
  </tr>
  <tr>
    <td>Pyspellchecker</td>
    <td>97.59%</td>
    <td>55.87%</td>
    <td>55.45%</td>
    <td>21.73%</td>
    <td>63.79%</td>
    <td>57.85%</td>
    <td>3.23%</td>
    <td>32</td>
  </tr>
  <tr>
    <td>Autocorrect</td>
    <td>100.00%</td>
    <td>56.04%</td>
    <td>56.04%</td>
    <td>23.62%</td>
    <td>64.81%</td>
    <td>44.66%</td>
    <td>8.84%</td>
    <td>42</td>
  </tr>
  <tr>
    <td>Textblob</td>
    <td>100.00%</td>
    <td>56.04%</td>
    <td>56.04%</td>
    <td>28.03%</td>
    <td>61.63%</td>
    <td>26.06%</td>
    <td>14.83%</td>
    <td>10</td>
  </tr>
</table>

## Analyzed tools overview

### Tool 1

### Tool 2

### Tool 3

## Conclusion