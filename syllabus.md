---
authors:
- 'Ganesh Katrapati `ganesh.katrapati@research.iiit.ac.in`\'
title: NLP Monsoon 2016 Syllabus
...

Duration
========

-   Classes : 24 (+2 Counting Mids)

-   Weeks :  12

Format
======

Paper & Pen Exercises
---------------------

-   These are light-load assignments that can be potentially done with a
    paper and a pen unless explicitly specified.

-   They are due automatically before the next class unless explicitly
    specified.

Course Timeline
===============

Week 1
------

### Class 1 : Introduction to NLP

-   **Pen & Paper Exercise** : Take a random article from the web,
    tokenize it. Explain what delimiters you used.

### Class 2 : Tokenization

#### 

Some Papers :

-   http://www.delph-in.net/courses/07/nlp/Gre:Tap:94.pdf

-   http://www.aclweb.org/anthology/P11-2008.pdf : Under the section
    [tagset] for discussion on twitter data

#### 

**Assignment [1]** : Twitter tokenization\

#### 

**P&P Exercise :** How can I predict the next word ?

Week 2
------

### Class 1 : Language Models

#### 

**Description** : Introduction to LM, Markov assumptions, N-Grams,
Probability of a sentence

#### 

**P&P** : Look at these sentences:

-   <span>1.</span> Mary had a little lamb

-   <span>2.</span> The little lamb had a friend

-   <span>3.</span> Mary had the little lamb.

-   <span>4.</span> \* Mary had friend little lamb

-   **a.** Sentence 3 & 4 will get 0 probability. While 4 is
    ungrammatical, 3 is perfectly alright. So now, how do we encode this
    into LM ?. Think of it this way too : for any a, b in sentence S; if
    we do not have P(a|b) but, have probabilities for all other n-grams
    in S; Can we still get the probability of the sentence some how ?

-   **b.** Take the sentence “Mary had one little lamb” : From the
    corpus above, we do not have the trigram $<$one little lamb$>$ but,
    we do have the bigram $<$little lamb$>$. Can we estimate
    $P(lamb|one\,\,little)$ by $P(lamb|little)$ ?. If so, will our
    probability estimates be correct ?. Think the appropriate ways to
    incorporate bigram knowledge in this scenario.

* * * * *

#### 

**Assignment [2]** : Prepare a set of sentences which are word &
sentence tokenized (you can possibly use OpenNLP/Stanford tokeniser).
Format your sentences with sentence open & sentence close tags
$(<s>, </s>).$ Now, for any given word/token can you estimate, whether
that is the sentence-ending token ?

-   Use n-grams for $n <= 6$ and observe how successful each ’n’ is in
    this task.

-   **2b** : Using $n <= 6$, generate sentences using LM probabilites.
    What do you observe ?

### Class 2 : Simple Smoothing

#### 

**Description**: Laplace, Jelinek & Heldout smoothing

#### 

**P&P**: Take the article for NLP in both simple english wikipedia and
from the normal english wikipedia. Do separate LM for both texts.

-   Observe the zipf tails for the texts: Which one is longer ?.

-   One way to talk about the ’new-ness’ of the language is if it
    creates and adapts new words. In that measure, which of the wikis is
    more ’new’ ?

-   In Laplace (Add-One) Smoothing, We expect that any word can follow
    any word atleast once. So, even if $(A|B)$ is not observed,
    $C(A|B) >= 1$. The probability mass of $V$ is added while computing
    the new probability ($C = C/C+V$). In the light of the above two
    questions : Is it okay to follow Laplace with the same $V$ (Possibly
    the whole english vocabulary) for the both wikis ?. Should we expect
    that any word will follow any other word regardless of the
    languages’/text’s degree of new words ?

Week 3
------

### Class 1 : Smoothing Continued

#### 

**Description**: Witten-Bell, Good-Turing, Kneser-Ney

#### 

**Reading :** Chapter 6; J&M

#### 

**Assignment [3]** :

-   Take texts of 5 different authors (gutenberg.org) Or, 5 articles
    each from 5 different topics.

    -   gutenberg.org has some the worlds most popular books.

    -   Choose authors from different time/places/writing style.

-   Do LM & Smoothing for each of these topics/authors separately

-   Plot the log-log curve (frequency vs rank) of all these different
    LMs on to one graph

-   Analyse the graph. What part of the zipf is same/different ?

-   Also look at the zipf curve of each topic/author (this time Id vs
    Frequency). Looking at the differences, given a new distribution (a
    new zipf curve) can we classify the text as to which author it
    belongs to ?.

### Class 2 : Text Classification & Naive Bayes

#### 

**Description**: Bayes theorem, Classification : Classes & Features,
Text Classification, Conditional Independence, Smoothing.

#### 

**Presentation: ** https://goo.gl/tsoj10

#### 

**Assignment [4] - POS Tagging** :

-   Using the naive bayes; classify words by their part-of-speech.

    -   English :

        -   Sample of PTB & Brown : http://www.nltk.org/book/ch02.html
            (See under : Annotated Text Corpora)

        -   MASC Corpus : http://www.anc.org/data/masc/

    -   Indian Languages : You can get this from tikiwiki

-   (Also a **P&P**) Words vs POS Tags is an ambiguous relationship. The
    word ’run’ is a noun/verb depending on the context.

    -   In naive bayes, the prior for the class is unconditional :
        $P(C)$. But suppose this depends on something else: In this
        case, the probability that a tag is ’verb’ depends on the
        previous tag: If it is a determiner it is likely to be a noun;
        if it is a noun/adverb; it is a verb. How can we incorporate
        this into the prior ?

    -   **PS** : If you can’t submit the assignment by next class,
        please sumbit the **P&P** part by the next class.

**Somewhere here, we also should have the LM Quiz (Mid Exam ? : 3 hrs 4
Questions)**

Week 4
------

### Class 1 : Part of Speech & Tagging

#### 

**Description:** Taking a deeper look into POS, Understanding the
problems in making a tagset & POS tagging, HMM, Difference between NB &
HMM (Single vs Structured Prediction & **How to know what to use for
what ?**), Transition & Emission probabilities, Noisy channel, Why is it
hidden ?.\
**!!** Need Ideas on **P&Ps**

### Class 2 : Viterbi & Trellis

#### 

**Reading :** Chapter 9-10, Manning & Schutze

#### 

**Assignment [5] - Morphology** :

-   **Heads up !!** for people who have no idea what morphology is; Take
    a look at this : https://goo.gl/tu7oCq

-   **Part 1 : Segmentation** : Given a word, separate it into morphemes
    and the stem. For example: unknowingly $\rightarrow$ un + know + ing
    + ly.

    -   Because English is fusional and has a lot of irregular forms,
        often, words cannot be separated into various morphemes. So,
        take an agglutinative language (Telugu, Tamil, Kannada,
        Malayalam, Turkish etc)

    -   You can also try Hindi but it will not be as clear.

    -   Prepare a set of words and segment them. (And yes, you can share
        the data. If you pick any language you do not know; either try
        and pair up with the person who does know or, ask another team
        for the data)

    -   Using the algorithms & methods in the classes before, develop a
        statistical morphological segmentor.

    -   **Hint !:** For each character, can we determine if it is a part
        of morph/stem ?. For example : $P(part-of-morph|'n')$ will be
        high given that it is in the middle of ’i’ and ’g’.

-   **Part 2: Morphanalysis :** Given a word such as ’cats’, a
    morphanalyser should give the output that it is a plural. (This
    should not just work with plurals but also all other types of
    morph-information; verb tense for instance)

    -   For any language (better to pick the same language as above),
        take a set of words ($\sim$ 200-300) and manually tag them for
        any morph information they might contain : For example,

        -   STEM for words which are bare stems (know, do, computer)

        -   PL for plurals (cats, dogs, babies)

        -   PST for past tense (waited, rated etc)

        -   PRG for progressive (waiting, breathing)

    -   If there is more than one morph-information, append the tags.

    -   Use this tagged resource and the algorithms learnt in the above
        class, build a morphanalyser.

    -   **Hint !:** For POS tagging, we used the entire word as a
        feature for determining the POS : $P(Tag|Word)$ but, for
        morphology we cannot (Otherwise we defeat the purpose : A
        morphanalyser does not want to store all the words !!). What
        will be the feature for morphanalysis ?.

-   **Describe the nature of each problem and describe which
    algorithm/method you used and why ?**

Week 5
------

### Class 1 : Morphology

#### 

**Description** : Morphology, Stemming, Lemmatization, FST based
morphanalyser, tries.

#### 

**Reading :**

-   Morphanalysis chapter in NLP : Paninian Perspective

-   https://goo.gl/BhDqao

#### 

**P&P :** Can we do morph-segmentation with out supervision ?. If so,
try and develop an algorithm.

### Class 2 : Statistical & Unsupervised Morphology

#### 

**Description** :

-   **Statistical** : Discussion & Solution to **Assignment [5]**. Which
    model to use for what ?.

-   **Unsupervised** : Rule generation & Pruning low-probable rules.
    (??)

#### 

**Reading :**

-   Morfette :
    http://www.lrec-conf.org/proceedings/lrec2008/pdf/594\_paper.pdf

-   Malladi et al : http://www.aclweb.org/anthology/W13-4914.pdf

Week 6
------

### Class 1 : Generative vs Discriminative Models

#### 

**Description**: The ml-quadrilateral\
\
![image](quad)

**Do we need assignments here ?**

### Class 2 : Chunking & Constituency

#### 

**Description** : Modeling Grammaticality, Why trigrams are not enough
?. Notion of chunk (Independent local grammaticality vs n-grams’
Dependent local grammaticality), Notion of chunk head, Notion of
constituent (Recursive local grammaticality), CFG, top-down and
bottom-up parsing.

#### 

**Reading :** J&M Chapter 9

#### 

**Assignment [6] :** Develop a chunker.

-   To get a more comprehensive understanding of chunking and chunk
    types see : http://ltrc.iiit.ac.in/tr031/posguidelines.pdf

-   Pick a language, annotate $\sim$ 100-150 sentences (Dont worry, you
    can pool the resources) for chunk boundaries & types.

-   Using the algorithms learnt in the classes before, develop a
    chunker.

-   Use all other linguistic resources we have dealt with previously :
    POS, Morph etc.

-   Data

    -   English : https://cogcomp.cs.illinois.edu/page/resource\_view/40

    -   Indian Languages : From tikiwiki

-   From the chunk-annotated corpora develop a chunk-level LM.

    -   First make an LM for chunk tags.

    -   Generate some chunk-sequences from that LM. are they grammatical
        ?.

    -   Make chunk-tag specific LMs i.e.
        $P(word_i|word_{i-1},chunk-tag)$ for each word.

    -   Now, given a chunk-tag, you can generate words in a chunk.

    -   Combine all of this and you get a chunk-based LM generation.

#### 

**P&P :**

-   Take 5 sentences each from English and any other Indian Language
    (This makes 10 sentences).

-   Write CFGs for both languages so that they can generate these
    sentences.

Week 7
------

### Class 1 : Constituency Parsing

#### 

**Description :** Problems with vanilla top-down and bottom up parsing,
CNF/2NF & Why these are necessary ?, CYK Parsing (Structured Prediction
over Trees). Limitations : Ambiguity (PP Attachment for example)

#### 

**Reading :** J&M Chapter 10

#### 

**P&P :**

-   If there are many parse trees possible for a given sentence and a
    grammar, which should you choose ?

-   Using the grammar developed in the previous **P&P** (Or any other
    grammar; It just needs to contain some ambiguity); Develop a CYK
    variant which generates a sentence given the start symbol.

-   How essential is CNF/2NF for CYK ?. Can CYK work without a CNF/2NF
    ?. If yes, describe the general idea.

### Class 2 : PCFGs & Induction

#### 

**Description :** Induction from the treebank, PCFGs & Resolution to
multiple trees problem, PCYK

#### 

**Reading :** J&M Chapter 12, same chapter in M&S

#### 

**Assignment [7] :** Two-Stage Constituency Parsing

-   **Part A:**

    -   Assume chunked sentences are the input.

    -   Develop a CFG based on chunk tags

    -   Implement CYK parser to parse chunk-tag CFG.

    -   **Problem :** In a *normal* PCFG+CYK, For each leaf production
        too, you have a probability : For instance
        $ N \rightarrow boy\,|\,girl\,|\,book\,|\,pen\,\,0.25$. When you
        start from the chunk, where do the probabilities come from ?.

    -   **Problem :** In a *normal* PCFG+CYK, a leaf can go to multiple
        non-terminals : For instance
        $ N \rightarrow  book\,\,0.1 \,\,\&\,\, V \rightarrow book\,\, 0.3$.
        Is this possible with chunks also ?

-   **Part B**: Make a PCFG and implement CYK with it.

-   Compare **A** and **B**. Prepare a detailed analysis on the both
    systems.

Week 8
------

:

### Class 1 : Drawbacks of PCFGs and the Way Forward

-   Three Generative Lexicalized models for parsing : Collins :
    http://dl.acm.org/citation.cfm?id=979620

-   Accurate UnLexicalised parsing : Klien & Manning :
    http://dl.acm.org/citation.cfm?id=1075150

-   Immediate Head Parsing : Charniak :
    http://www.aclweb.org/anthology/P01-1017

**Lexicalization vs Unification ?**

### Class 2 : Catchup Class

:

Week 9
------

### Class 1 : Introduction to Dependency Parsing

#### 

**Description:** Introduction, Comparision to Constituency (How it
solves some of the problems of Constituency parsers), Indian Languages,
Karakas, Link Parser, Shift-Reduce Parsing, Projectivity

#### 

**Assignment [8] :** Writing an oracle

-   Data : The Hindi Treebank (HTB)

-   Tools : SSF-API for C & Python

-   Task : Given a verb, can we figure out to which nouns it attaches
    itself to. If it does, what is the label of such attachment.

-   From the HTB, for each sentence look at the dependency relations
    between a verb-chunk and a noun-chunk. This is your training data.
    Make a model which learns these relationships.

#### 

**P&P :**

-   We all now have talked about the difference between constituency and
    dependency parsing strategies. In constituency we have dealt solely
    with CFG/PCFGs. Do you think CFGs are exclusive to
    constituency/phrase-structured parsing ?. Can we dependency be
    described in it ?.

-   

### Class 2 : Dependency parsing part two

#### 

**Description:** MALT & MST parsers

#### 

**Reading :**

-   For the previous P&P :
    https://www.ps.uni-saarland.de/ rade/papers/dg.pdf (Simpler version
    of Gaifman et al)

-   MALT Parser Paper

-   MST Parser Paper

#### 

**P&P : ** Devise algorithms to convert phrase structured tree to
dependency tree and vice versa. Elucidate on the problems faced.

Week 10
-------

### Class 1 : Lexical Semantics & Distributional Semantics

#### 

**Description:** Meaning as truth and Meaning as a distribution. Tasks :
PP Attachment, WSD, SRL, MWE, Noun Compounds,

Grading Scheme
==============

Week 10: semantics (lexical - wsd, odd-one-out) Week 11: generation Week
12: machine translation

9 : 1

10 : word vect & pos ? 11

12
