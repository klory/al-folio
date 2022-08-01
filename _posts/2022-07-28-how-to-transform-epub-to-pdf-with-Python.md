---
layout: post
title: How to transform epub with images to pdf using Python
description: Epub to PDF
date: 2022-07-28
comments: true
---

## Why I do it

I use iPhone and iPad to read mangas every now and then, but sometimes Epub format can be annoying, either they can not be opened on iPhone or they have some blank pages in between. Changing to PDF can solve most of the problem it seems.

## How to do it in Python

```python
import ebooklib
from ebooklib import epub
from PIL import Image
import io

fname = f'dragon_ball_1.epub'
book = epub.read_epub(fname)

images = []
for image in book.get_items_of_type(ebooklib.ITEM_IMAGE):
    image = Image.open(io.BytesIO(image.content))
    images.append(image)

pdf_path = f"dragon_ball_1.pdf" 
images[0].save(
    pdf_path, "PDF" ,resolution=100.0, save_all=True, append_images=images[1:]
)
```

It takes less than 3 minutes to transform a 172MB epub file with 1256 pages on my 2019 MBP16.