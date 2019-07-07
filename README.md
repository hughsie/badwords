badwords
========

A simple list of bad words in different locales.

The idea here is we have a locale-specific list of tokens than can be used to
flag suspicious user-submitted content when the locale is known.

When getting banned tokens from this list the suggested fallback path is
`language_REGION` -> `language` -> `en`, e.g. `es_CO` -> `es` -> `en`.

Some rules on the data sections:

File Format
===========

Locale
------

Either a `language_REGION` or `language`, for instance `es_CO` or `de`. Where a
bad word is applicable to more than one region, just remove the region code so
it matches for all regions.

If the spelling of a badword is different between regions (e.g.
`en_GB:arsehole` v.s. `en_US:asshole` either just use the correct language code
or if the word is unambiguous in all regions, use just the locale code with both
forms listed, e.g. `en:arsehole/asshole`.

Value
-----

A single lowercase word, split using forward slashes if there exists other forms,
for instance male/female, past/future or singular plural.
Multiple words forming part of a sentence are not allowed.

Description
-----------

A small single line generally lower case description of the `value`, using
brackets and quotes to a minimum and a semicolon where more description is
required.

Severity
--------

This tells the consumer *how* bad the word actually is, for instance if it's
just something you wouldn't say in polite conversation, or something that
should never be uttered in any circumstances.

The scale I've used here is just three numbers to avoid too much discussion:

 * 0: No data available
 * 1: Sometimes an acceptable word to say to your parents
 * 2: Sometimes an acceptable word to say to friends of same age
 * 3: Never acceptable to use

Consumers
=========

The list of badwords is being used by:

 * Open Desktop Ratings Service (ODRS): https://odrs.gnome.org/
