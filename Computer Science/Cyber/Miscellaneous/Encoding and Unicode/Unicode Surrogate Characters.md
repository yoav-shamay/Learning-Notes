Used to encode characters `> 0x10000` (more than 2 bytes).
To encode such a character, first subtract `0x10000`. Then split to low 10 bits and high 10 bits.
A surrogate character is used for each part - a high surrogate for the higher bits than low characters for the low 10 bits.
the high surrogate is `0xd800 + (high 10 bits)`
the low surrogate is `0xdc00 + (low 10 bits)`.