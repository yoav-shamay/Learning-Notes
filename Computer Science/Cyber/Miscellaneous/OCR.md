## pytesseract
python interface to tesseract.
Good and easy to use.
Does lots of mistakes though.
Usage: `pytesseract.image_to_string(pillow_image)`.
Can put some options by adding `config=config_str` parameter.
### Config Options
- `--psm 8` - single word
- `-c tessedit_char_whitelist=abcdef` - char whitelist
### Good configs
- Captcha: `"--psm 8 --oem 3 -c tessedit_char_whitelist=ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789"` - single words, good engine, only alphanumeric