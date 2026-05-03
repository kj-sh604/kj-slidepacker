# kj-slidepacker

> to be used with exports from [sent-web](https://sent-web.site), LaTeX Beamer, or any other source of PDF presentations.

converts a `.pdf` presentation into a "fake" `.pptx` by rendering each page as an image and pasting it onto a blank slide.

output slides are **not editable**, this is intentional. 

the goal is just to get a pdf into pptx format for corporate compliance purposes (e.g., when someone absolutely **NEEDS** a `.pptx` and would go crazy if the file is not sent with an extension that says **• P P T X**).

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

# set render resolution (defaults: 150 dpi standard, 100 dpi with -1)
./src/slidepacker deck.pdf --dpi 200

# tune jpeg quality (default: 98)
./src/slidepacker deck.pdf --jpeg-quality 100

# stack all pages on one slide and click through with no animation delay
./src/slidepacker deck.pdf -1
```

## as a lib

```python
import sys
sys.path.insert(0, "path/to/kj-slidepacker/src")

import slidepacker
slidepacker.pack("deck.pdf", "deck.pptx", dpi=200)

# lower quality for smaller files
slidepacker.pack("deck.pdf", "deck.pptx", dpi=200, jpeg_quality=90)

# one-slide click-through mode
slidepacker.pack("deck.pdf", "deck.pptx", dpi=200, one_slide=True)
```

## license

0BSD - see [LICENSE](LICENSE)
