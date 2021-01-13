---
layout: default
title: Inflectors
nav_order: 9
---


# Inflectors

## Nouns

Nouns can be pluralized/singularized with a `NounInflector`:

```javascript
var natural = require('natural');
var nounInflector = new natural.NounInflector();
```

To pluralize a word (outputs "radii"):

```javascript
console.log(nounInflector.pluralize('radius'));
```

To singularize a word (outputs "beer"):

```javascript
console.log(nounInflector.singularize('beers'));
```

Like many of the other features, String can be patched to perform the operations
directly. The "Noun" suffix on the methods is necessary, as verbs will be
supported in the future.

```javascript
nounInflector.attach();
console.log('radius'.pluralizeNoun());
console.log('beers'.singularizeNoun());
```

## Numbers

Numbers can be counted with a CountInflector:

```javascript
var countInflector = natural.CountInflector;
```

Outputs "1st":

```javascript
console.log(countInflector.nth(1));
```

Outputs "111th":

```javascript
console.log(countInflector.nth(111));
```

## Present Tense Verbs

Present Tense Verbs can be pluralized/singularized with a PresentVerbInflector.
This feature is still experimental as of 0.0.42, so use with caution, and please
provide feedback.

```javascript
var verbInflector = new natural.PresentVerbInflector();
```

Outputs "becomes":

```javascript
console.log(verbInflector.singularize('become'));
```

Outputs "become":

```javascript
console.log(verbInflector.pluralize('becomes'));
```

Like many other natural modules, `attach()` can be used to patch strings with
handy methods.

```javascript
verbInflector.attach();
console.log('walk'.singularizePresentVerb());
console.log('walks'.pluralizePresentVerb());
```
