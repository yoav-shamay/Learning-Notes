- View spectogram in Audacity
- Each audio file is actually a sequence of numbers. 
## Wav files
- `wav` files can have multiple channels like left / right
Converting `wav` files to numbers:
```python
from scipy.io import wavfile
sr, data = wavfile.read("main.wav")   # data is a NumPy array, sr is sample rate
```
Creating `wav` file from numbers: `wavfile.write(filename, sr, data_np_array)`