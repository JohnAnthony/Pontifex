Introduction
============

This is an implementation of the Pontifex/Solitaire hand encryption algorithm as used in Neal Stephenson's excellent book "Cryptonomicon" and created by Bruce Schneier. It's written in Scheme for the Guile interpreter specifically, but should be incredibly easy to adapt to any other interpreter.

Usage
=====

There are 3 major functions you will want to use.

Getting your key
----------------

Your interface with the virtual "deck of cards" is via the procedure pontifex-random-key, which will return a new shuffled deck.

```
scheme@(guile-user)> (pontifex-random-key)
$2 = (eight-of-hearts seven-of-spades ace-of-hearts nine-of-diamonds six-of-clubs king-of-diamonds two-of-clubs four-of-diamonds four-of-spades queen-of-spades four-of-clubs jack-of-spades ten-of-diamonds ace-of-spades three-of-clubs two-of-spades five-of-hearts nine-of-hearts seven-of-hearts queen-of-hearts two-of-hearts ten-of-hearts ace-of-diamonds seven-of-diamonds queen-of-diamonds ten-of-clubs six-of-spades eight-of-spades king-of-clubs five-of-clubs three-of-hearts nine-of-clubs jack-of-hearts nine-of-spades joker-b five-of-spades six-of-diamonds eight-of-clubs king-of-hearts three-of-spades six-of-hearts ten-of-spades eight-of-diamonds five-of-diamonds queen-of-clubs four-of-hearts ace-of-clubs king-of-spades jack-of-clubs joker-a jack-of-diamonds seven-of-clubs two-of-diamonds three-of-diamonds)
```

You can also generate this data structure manually or through any means you wish - it is effectively just a representation of your shared key with somebody else.

Encrypting your text
--------------------

You encrypt your text simply with pontifex-encrypt, your plaintext in the form of a string and your deck of cards as a key

```
scheme@(guile-user)> (pontifex-encrypt "hellosecretworld" $2)
$3 = "YGDMKCBSIBLKPKOV"
```

Decrypting your text
--------------------

You decrypt with the partnered decrypt function by simply entering your cyphertext and key

```
scheme@(guile-user)> (pontifex-decrypt "YGDMKCBSIBLKPKOV" $2)
$4 = "HELLOSECRETWORLD"
```
