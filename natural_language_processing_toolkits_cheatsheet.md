# Natural Language Processing Toolkit Notes

Following along with [Natural Language Processing with Python](http://nltk.org/book/).

## 1.1 - Computing with Language: Texts and Words



### Searching Text

#### Search text for every occurence of word:

    text1.concordance('foo')

#### Find synonyms:

    text1.similar('foo')

#### Examine just the contexts that are shared by two or more words:

    text1.common_contexts(['foo', 'bar'])

#### Dispersion Plot:

    text1.dispersion_plot('foo', 'bar', 'tar', 'car')

#### Generate random text:

    text1.generate()



### Counting Vocabulary

#### Count Vocabulary:

    len(text1)

#### Count occurance of word:

    text1.count('foo')

#### See all words from text:

    set(text1)



## 1.3 - Computing with Language: Simple Statistics

### Frequency Distributions

#### Frequency Distribution:

    FreqDist(text1)

#### Plot Frequency Distribution (most common words):

    FreqDist(text1).plot(50, cumulative=True)

#### Hapaxes (least common words):

    FreqDist(text1).hepaxes()

#### Find Long Words:

    sorted([w for w in set(text1) in len(w) > 15])

#### Find Long and Common Words:
It is postulated that words of greater length than 7 characters and a count of occurence greater than 7 are the common content-bearing words of a text.

    fdist = FreqDist(text1)
    sorted([w for w in set(text1) if len(w) > 7 and fdist[w] > 7])

### Collocations and Bigrams

> A collocation is a sequence of words that occur together unusually often. Thus red wine is a collocation, whereas the wine is not. A characteristic of collocations is that they are resistant to substitution with words that have similar senses; for example, maroon wine sounds very odd.

#### Bigrams:

Generate a list of word pairs from a text

    bigrams(text1[100:120])

#### Collocations

Frequent bigrams.  Common pairings of words.

    text1.collocations()

#### Counting Other Things

Count word lengths

    >>> fdist = FreqDist([len(w) for w in text1])
    >>> fdist.items()  # Get all word lengths and their count of occurence
    [(3, 50223), (1, 47933), (4, 42345), (2, 38513), (5, 26597), (6, 17111), (7, 14399), (8, 9966), (9, 6428), (10, 3528), (11, 1873), (12, 1053), (13, 567), (14, 177),
    (15, 70), (16, 22), (17, 12), (18, 1), (20, 1)]
    >>> fdist.max()  # Get most common word length
    3
    >>> fdist[3]  # Get count of occurence for three letter words
    50223
    >>> fdist.freq(3)  # Get percentage value for the occurrence of three letter words in text
    0.19255882431878046

#### Table 1-2. Functions defined for NLTK’s frequency distributions

> Example | Description
> --- | ---
`fdist = FreqDist(samples)` | Create a frequency distribution containing the given samples
> `fdist.inc(sample)` | Increment the count for this sample
> `fdist['monstrous']` | Count of the number of times a given sample occurred
> `fdist.freq('monstrous')` | Frequency of a given sample
> `fdist.N()` | Total number of samples
> `fdist.keys()` | The samples sorted in order of decreasing frequency
> `for sample in fdist:` | Iterate over the samples, in order of decreasing frequency
> `fdist.max()` | Sample with the greatest count
> `fdist.tabulate()` | Tabulate the frequency distribution
> `fdist.plot()` | Graphical plot of the frequency distribution
> `fdist.plot(cumulative=True)` | Cumulative plot of the frequency distribution
> `fdist1 < fdist2` | Test if samples in fdist1 occur less frequently than in fdist2
