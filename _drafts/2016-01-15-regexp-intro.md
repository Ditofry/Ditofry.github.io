---
layout: post
title:  "Regexp Basics"
categories: regular-expressions code reference
---
#### things in the brackets are character classes
[chb]at  // matches three words

#### ranges
[a-fA-F0-9] // matches hex numbers

#### Metacharacters
h.t   // "." signifies a match with and character
Server: gws\r\n
*Aside* curl will copy url, curl with -I will get you the headers
\s // white space
\w // any alpha-numeric and "_", shorthand for [A-Za-z0-9_]
\W // NOT any alpha-numeric and "_", shorthand for [^A-Za-z0-9_]
\d // [0-9]
\D // [^0-9]

gmail|yahoo  // gmail or yahoo


#### Repetition:
[]? = 0 or 1
[]+ = 1 or more
[]* = 0 or more
[]{0,42} = 0-42
[]{42} = 42

#### Grouping
www\.(gmail|yahoo)\.com

#### Anchors
^cat$

#### Examples
^hubot@gmail\.com$  requires that hubot be at the beginning of the string, alone, in other words.

#### Misc
Regexps are greedy by default (think of the hubotathubotatgmaildotcom)

#### Questions
 - difference between ^ in a c-class and ^ as an anchor
