
# wink-naive-bayes-text-classifier

> Configurable [Naive Bayes](https://en.wikipedia.org/wiki/Naive_Bayes_classifier) Classifier for text with cross-validation support

### [![Build Status](https://api.travis-ci.org/decisively/wink-naive-bayes-text-classifier.svg?branch=master)](https://travis-ci.org/decisively/wink-naive-bayes-text-classifier) [![Coverage Status](https://coveralls.io/repos/github/decisively/wink-naive-bayes-text-classifier/badge.svg?branch=master)](https://coveralls.io/github/decisively/wink-naive-bayes-text-classifier?branch=master)

<img align="right" src="https://decisively.github.io/wink-logos/logo-title.png" width="100px" >

**wink-naive-bayes-text-classifier** is a part of **[wink](https://www.npmjs.com/~sanjaya)**, which is a family of Machine Learning NPM packages. They consist of simple and/or higher order functions that can be combined with NodeJS `stream` and `child processes` to create recipes for analytics driven business solutions.

Classify text, analyse sentiments using wink-naive-bayes-text-classifier, which inherently supports cross validation.

## Installation
Use **[npm](https://www.npmjs.com/package/wink-naive-bayes-text-classifier)** to install:
```
npm install wink-naive-bayes-text-classifier --save
```


## Usage
```javascript

// Load Naive Bayes Text Classifier
var nbc = require( 'wink-naive-bayes-text-classifier' )();
var nlp = require( 'wink-nlp-utils' );

// Setup preparation tasks
nbc.definePrepTasks( [
  nlp.string.tokenize0,
  nlp.tokens.removeWords,
  nlp.tokens.stem
] );
// Train!
nbc.learn( 'i want to prepay my loan', 'prepay', true );
nbc.learn( 'i want to close my loan', 'prepay', true );
nbc.learn( 'i want to foreclose my loan', 'prepay', true );
nbc.learn( 'i would like to pay the loan balance', 'prepay', true );

nbc.learn( 'i would like to borrow money to buy a vehice', 'autoloan', true );
nbc.learn( 'i need loan for car', 'autoloan', true );
nbc.learn( 'i need loan for a new vehicle', 'autoloan', true );
nbc.learn( 'i need loan for a new mobike', 'autoloan', true );
nbc.learn( 'i need money for a new car', 'autoloan', true );
// Consolidate all the training!!
nbc.consolidate();
// Start predicting...
console.log( nbc.predict( 'I would like to borrow 50000 to buy a new audi r8 in new york' ) );
// -> autoloan
console.log( nbc.predict( 'I want to pay my car loan early' ) );
// -> prepay

```

## Need Help?
If you spot a bug and the same has not yet been reported, raise a new [issue](https://github.com/decisively/wink-naive-bayes-text-classifier/issues) or consider fixing it and sending a pull request.


## Copyright & License
**wink-naive-bayes-text-classifier** is copyright 2017 GRAYPE Systems Private Limited.

It is licensed under the under the terms of the GNU Affero General Public License as published by the Free
Software Foundation, version 3 of the License.