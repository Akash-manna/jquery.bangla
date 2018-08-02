# Bangla Input Tools

<p>
  [![Build Status](https://travis-ci.org/dipu-bd/jquery.bangla.svg?branch=master)](https://travis-ci.org/dipu-bd/jquery.bangla)
  [![NPM Downloads](https://img.shields.io/npm/dt/jquery.bangla.svg?style=flat-square)](https://www.npmjs.com/package/jquery.bangla)
  [![Code Climate](https://img.shields.io/codeclimate/github/dipu-bd/jquery.bangla.svg?style=flat-square)](https://codeclimate.com/github/dipu-bd/jquery.bangla)
  [![Dependencies]("https://david-dm.org/dipu-bd/jquery.bangla.svg?style=flat-square)](https://david-dm.org/dipu-bd/jquery.bangla)
  [![License](https://img.shields.io/npm/l/vue-weather-widget.svg?style=flat-square)](https://github.com/dipu-bd/vue-weather-widget/blob/master/LICENSE)
</p>

A versatile bangla input tools for the web

**Live Demo**: https://dipu-bd.github.io/jquery.bangla/ 

## Installation

```bash
npm i --save jquery jquery.bangla
```

## Usage

```javascript
import 'jquery.bangla';

// Or,
require('jquery.bangla');

// Then, on some editable elements...

$('input[type="text"]').bangla(); // input box

$('textarea').bangla(); // text area

$('div[contenteditable="true"]').bangla(); // content editable div

$('.note-editable').bangla() // summer-note (a free WYSWYG editor)
```

## Usage (Browser)

1. Clone this repository and go to project folder.
2. Perform `npm install`
3. Then `npm run build`
4. Copy the script file inside `dist/` folder to your static assets directory
5. See the example in [gh-pages branch](https://github.com/dipu-bd/jquery.bangla/blob/gh-pages/index.html) for usage.

## API

### Initial Configuration

You an pass the following configs during initialization (all configs are optional):

```javascript
// all the default values are given here
$('<some-element-selectoor>').bangla({
  enable: false,
  maxSuggestions: 10,
  disableSuggestion: false,
  storeKey: '__avro--candidates',
  store: window.localStorage,
  provider: /* see below */
})
```

#### Config: `enable`

Pass `true` to enable bangla right after initialization.

#### Config: `maxSuggestions`

The maximum number of suggestions that user will see for a word.

#### Config: `disableSuggestion`

Pass `true` if you do not want to display the suggestion box.

#### Config: `storeKey`

The key that is used for storing candidate words.

#### Config: `store`

The storage to save candidate words. A cadidate word is a bangla word that user had select against an english word. In the next suggestion box for that english word, the cadidate word will be automatically selected.

The store should haeve two fields:

- `getItem(key)`: Returns the value given the key
- `setItem(key, val)`: Stores the value against the key to retriee it later.

#### Config: `provider`

By default, Avro Phonetic from https://github.com/omicronlab/avro-pad is used. But you can define your own provider. A provider should have three fields.

- `suggest(word)`: This will return an object containing `words` field. The field `words` is an array of possible bangla word for the given english word.
- `candidate(word)`: This will return previously selected bangla word for the english input.
- `commit(word, bangla)`: It will save the candidate bangla word for an english word.

### Methods

You can customize the input tool after initialization:

- `$('input').bangla('toggle')`: Toggles the input option between bangla and english.
- `$('input').bangla('enable')`: Get whether the bangla is enabled
- `$('input').bangla('enable', true)`: Enables the bangla input
- `$('input').bangla('enable', false)`: Disable the bangla input, and enable english.

## License

> [Mozilla Public License Version 2.0](https://github.com/dipu-bd/jquery.bangla/blob/master/LICENSE)
