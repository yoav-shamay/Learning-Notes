A padding oracle attack on RSA.
See https://archiv.infsec.ethz.ch/education/fs08/secsem/bleichenbacher98.pdf
Also https://cryptopals.com/sets/6/challenges/48
The idea is to try to multiply by different values until the padding is valid.
Then we reduce the range accordingly.
We have a good chance to find a valid multiple, and it reduces the range significally.
