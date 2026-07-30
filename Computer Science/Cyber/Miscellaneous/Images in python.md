```python
from PIL import Image
import numpy as np
img = Image.open('img1.jpg')
img1_as_np_array = np.asarray(img) # can do operations like xor, sum easily
rgb = img.getpixel((i, j))
w, h = img.size
pixels_np_array = np.array(rgb_2d_array, dtype=np.uint8)
img = Image.fromarray(pixels_np_array)
img.save("out.jpg")
img.open()
```