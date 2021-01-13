---
layout: default
title: Phonetics
nav_order: 9
---

# Phonetics
Phonetic matching (sounds-like) matching can be done with the [SoundEx](http://en.wikipedia.org/wiki/Soundex),
[Metaphone](http://en.wikipedia.org/wiki/Metaphone) or [DoubleMetaphone](http://en.wikipedia.org/wiki/Metaphone#Double_Metaphone) algorithms

```javascript
var natural = require('natural');
var metaphone = natural.Metaphone;
var soundEx = natural.SoundEx;

var wordA = 'phonetics';
var wordB = 'fonetix';
```

To test the two words to see if they sound alike:

```javascript
if(metaphone.compare(wordA, wordB))
    console.log('they sound alike!');
```

The raw phonetics are obtained with `process()`:

```javascript
console.log(metaphone.process('phonetics'));
```

A maximum code length can be supplied:

```javascript
console.log(metaphone.process('phonetics', 3));
```

`DoubleMetaphone` deals with two encodings returned in an array. This
feature is experimental and subject to change:

```javascript
var natural = require('natural');
var dm = natural.DoubleMetaphone;

var encodings = dm.process('Matrix');
console.log(encodings[0]);
console.log(encodings[1]);
```

Attaching will patch String with useful methods:

```javascript
metaphone.attach();
```

`soundsLike` is essentially a shortcut to `Metaphone.compare`:

```javascript
if(wordA.soundsLike(wordB))
    console.log('they sound alike!');
```

The raw phonetics are obtained with `phonetics()`:

```javascript
console.log('phonetics'.phonetics());
```

Full text strings can be tokenized into arrays of phonetics (much like how tokenization-to-arrays works for stemmers):

```javascript
console.log('phonetics rock'.tokenizeAndPhoneticize());
```

Same module operations applied with `SoundEx`:

```javascript
if(soundEx.compare(wordA, wordB))
    console.log('they sound alike!');
```

The same String patches apply with `soundEx`:

```javascript
soundEx.attach();

if(wordA.soundsLike(wordB))
    console.log('they sound alike!');

console.log('phonetics'.phonetics());
```
