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

A detailed description of the dataset and the selected metrics is written in
the [notebook](https://github.com/diffitask/spell-checkers-comparison/blob/main/spell-checkers-comparison.ipynb). Also,
here you can find the code of how the analyzed spell checking tools work on test data and measurements of metrics for
each checker.

## Benchmarks
TODO: table

## Analyzed tools overview

### Tool 1

### Tool 2

### Tool 3

# Conclusion