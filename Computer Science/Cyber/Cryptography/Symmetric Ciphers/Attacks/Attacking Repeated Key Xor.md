Also: many time pad
Xor multiple plaintexts with same key, or xor a long plaintext with short key (practically the same).
TODO - prob have an existing better solution instead of my own scripts
- xortools - might do the automatic solving part for repeated key xor
## Option 1 - Interactive solver
See https://cryptopals.com/sets/3/challenges/19
Just guess the next letter manually according to English context
My (not so good) script for the case of multiple plaintexts with same key:
More features to implement if for some reason doesn't already exist: preview of how a letter will affect other texts, proper GUI
```python
cts = encrypt_plaintexts() # REPLACE THIS WITH HOWEVER YOU GET ct. SHOULD BE LIST OF bytes
key_len = max(map(len, cts))
options = [[] for _ in range(key_len)]
for i in range(key_len):
    alphabet = string.ascii_letters + " .,!?'\"-:;" + string.digits
    for option in range(256):
        valid = True
        for j in range(len(cts)):
            if len(cts[j]) > i:
                char = cts[j][i] ^ option
                if chr(char) not in alphabet:
                    valid = False
                    break
        if valid:
            options[i].append(option)

CHOSEN_STRING_COUNT = 3 # REPLACE THIS WITH THE NUMBER OF PARTIAL PLAINTEXTS YOU WANT TO SEE
cts_sorted = sorted(cts, key=len,reverse=True)
remaining_to_determine = []
for i, x in enumerate(options):
    if len(x) > 1:
        remaining_to_determine.append(i)
for i in remaining_to_determine:
    for k in range(CHOSEN_STRING_COUNT):
        ct = cts_sorted[k]
        template = ""
        for j in range(len(ct)):
            if len(options[j]) == 1:
                template += chr(ct[j] ^ options[j][0])
            elif j != i:
                template += "_"
            else:
                template += "*"
        print(template)
        print()
    first_options = []
    for x in options[i]:
        cur = []
        for j in range(CHOSEN_STRING_COUNT):
            if i < len(cts_sorted[j]):
                cur.append(chr(cts_sorted[j][i] ^ x))
        first_options.append(cur)
    if len(first_options) < 10:
        print("Options:", first_options)
    index = int(input("Enter the index of the string you guess a letter in: "))
    first_string_letter = input(f"Enter letter in {index} string: ")
    options[i] = [ord(first_string_letter) ^ cts_sorted[index][i]]

# now print all plaintexts
for ct in cts:
    decoded = []
    for i in range(len(ct)):
        decoded.append(ct[i] ^ options[i][0])
    print(bytes(decoded).decode())
```
## Option 2 - statistically
See https://cryptopals.com/sets/3/challenges/20, https://cryptopals.com/sets/1/challenges/6
First, find the key length and split according to it.
This should be the key length that minimizes the hamming distance between key cycles TODO test, how to.
Afterwards, we basically have the same xor with multiple texts.
The idea is to use the byte that maximizes the sum of frequency scores.
Also probably exists online (TODO) but meanwhile here's my solution:
download frequency scores online, for example from https://github.com/piersy/ascii-char-frequency-english/blob/main/ascii_freq.json
And this code:
```python
cts = encrypt_plaintexts() # REPLACE THIS WITH YOUR CIPHERTEXTS
key_len = max(map(len, cts))
options = [[] for _ in range(key_len)]
frequency_file = open("freq_scores.json", "r")
freq_json = frequency_file.read()
frequency_file.close()
freq_json_parsed = json.loads(freq_json)
ascii_score = {}
for entry in freq_json_parsed:
    ascii_score[entry["Char"]] = entry["Freq"]

key = b""
for i in range(key_len):
    maxi = 0
    best = -1
    for option in range(256):
        char = option.to_bytes()
        score = 0
        for ct in cts:
            if i >= len(ct):
                continue
            if option ^ ct[i] in ascii_score:
                score += ascii_score[option ^ ct[i]]
        if score > maxi:
            maxi = score
            best = char
    assert best != -1
    key += best

# now print all plaintexts
for ct in cts:
    decoded = []
    for i in range(len(ct)):
        decoded.append(ct[i] ^ key[i])
    print(bytes(decoded).decode())

```
Will go most of the way, can use manual editing afterwards.