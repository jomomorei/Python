### 1. Python PDF parser and analyzer

* PDFMiner: Python2.0

   Ref: https://github.com/euske/pdfminer

* PDFMiner3k: Python3.0
* PDFMiner.six: Python3.0

   Ref: https://github.com/pdfminer/pdfminer.six


## Extract a page from a pdf as a jpeg on WIN7

### Preparation
#### a. Install pdf2image 
```
pip install pdf2image
```
#### b. Install poppler
 1. Download zip file from [poppler for Windows](http://blog.alivate.com.au/poppler-windows/)
 
 1. Unzip to a new folder in your program files folder. For example: "C:\Program Files (x86)\Poppler".
 
 1. Add "C:\Program Files (x86)\Poppler\ __poppler folder__ \bin" to your SYSTEM PATH environment variable.
 
 1. Restart PC(if necessary).
 
### For single file single page

```Python
from pdf2image import convert_from_path
pages = convert_from_path("pdf file", 300)

for page in pages:
    page.save('out.jpg', 'JPEG')
 ```
:red_circle: _Here 'pdf file' is relative path._

### For general case: all pages for all files in given folder
```Python
import os
from pdf2image import convert_from_path

pdf_dir = r"PDF_Folder"
os.chdir(pdf_dir)

for pdf_file in os.listdir(pdf_dir):

    if pdf_file.endswith(".pdf"):

        pages = convert_from_path(pdf_file, 300)
        pdf_file = pdf_file[:-4]

        for page in pages:

            page.save("%s-page%d.jpg" % (pdf_file,pages.index(page)), "JPEG")
 ```
 

#### Reference :https://stackoverflow.com/questions/46184239/python-extract-a-page-from-a-pdf-as-a-jpeg
