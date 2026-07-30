A more general `lower` operation, used for generalized case insensitive comparison.
This can result in `true` when standard case insensitive comparison results in `false`.
An actual full list is https://searchfox.org/firefox-main/source/js/src/util/CaseFolding.txt
To find a match, for example for the letter `s`, see `LATIN CAPITAL LETTER S` expands to `0073`
Now see what else expands to `0073` by using Ctrl+F on `0073`
It shows that `LATIN SMALL LETTER LONG S` works.