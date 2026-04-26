# kj-slidepacker

> to be used with exports from [sent-web](https://sent-web.site), LaTeX Beamer, or any other source of PDF presentations.

converts a `.pdf` presentation into a "fake" `.pptx` by rendering each page as an image and pasting it onto a blank slide.

output slides are **not editable**, this is intentional. 

the goal is just to get a pdf into pptx format for corporate compliance purposes (e.g. sending to someone who **needs** a .pptx and would crazy if it's not sent with an extension that says • P P T X).

https://github.com/user-attachments/assets/649b6259-9c86-49fd-bba5-4431f051e82a

## deps

- python 3.13+ (probably works on older versions but not tested)
- [pymupdf](https://pypi.org/project/pymupdf/)
- [python-pptx](https://pypi.org/project/python-pptx/)

## install

```sh
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## usage

```sh
# output defaults to the same stem as the input
./src/slidepacker deck.pdf

# specify output path
./src/slidepacker deck.pdf out.pptx

# set render resolution (default: 150 dpi)
./src/slidepacker deck.pdf --dpi 200
```

## as a libr

```python
import sys
sys.path.insert(0, "path/to/kj-slidepacker/src")

import slidepacker
slidepacker.pack("deck.pdf", "deck.pptx", dpi=200)
```

## license

0BSD - see [LICENSE](LICENSE)
