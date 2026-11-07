Can be used to find the length of a key in repeating xor (or vigenere) cipher.

This is the chance that two characters in the text are the same.
Given a text, this is:
$$
\sum_{char} \frac{\operatorname{count}(char) \times (\operatorname{count}(char) - 1)}{len(len - 1)}
$$
Where $len$ is the length of the text, and $\operatorname{count}(char)$ is the amount of times $char$ appears in the text.
For a completely random text of english letters this is $1 / 26 \approx 0.03846$, but for actual English text, due to letter frequencies, this is around $0.066$.
Usually this is normalized - you divide by the expected random distribution ($1 / 26$), so random text is $1.0$, and English text is around $1.5 - 2.0$.

This metric is kept after substitution, this means that for the correct key length, this should be around the English text value, but for incorrect one it should be closer to the random letters value.

For XOR this is similar, but should consider spaces, punctuation and other characters, and the random text value is actually $1 / 256 \approx 0.003906$.