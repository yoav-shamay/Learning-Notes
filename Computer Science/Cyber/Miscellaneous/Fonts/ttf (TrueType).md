A font type.
## Parsing
Can be parsed using the `fonttools` library.
Opening:
```python
from fontTools.ttLib import TTFont
font = TTFont("Arial-custom.ttf")
```
## Components
### CMAP
This is a table that maps unicode endpoints to glyphs.
A font can have multiple cmaps, for different platforms.
### glyf
This is a table that contains the visual representation of glyphs.
### GSUB
Glyph Substitution Table.
A table that maps sequence of glyph to be substituted with another sequence of glyph.
Has multiple options inside, like single to single, multi to single, single to multi, include context and more.