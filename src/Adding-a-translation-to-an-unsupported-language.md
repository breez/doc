# Translating Breez into an unsupported language

To translate the Breez interface to a new language:
* [Click here](https://github.com/breez/breezmobile/tree/master/lib/l10n) for all the app strings.
* To add a new language, simply copy the _app_en.arb_ file and and change its suffix to the new [language's code](https://api.flutter.dev/flutter/dart-ui/Locale/languageCode.html). For example: 
  * English: app_en.arb
  * Portuguese: app_pt.arb
  * Spanish: app_es.arb
* Translate the strings into the new language.
* [Open a PR](https://github.com/breez/breezmobile/pulls) with the new _app_xy.arb_ file. 
* Our developers will review and integrate the new language to the Breez code base.
