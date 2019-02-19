## Extract a page from a pdf as a jpeg on WIN7

### Install pdf2image 
```
pip install pdf2image
```
### Install poppler
 1. Download zip file from [poppler for Windows](http://blog.alivate.com.au/poppler-windows/)
 
 1. Unzip to a new folder in your program files folder. For example: "C:\Program Files (x86)\Poppler".
 
 1. Add "C:\Program Files (x86)\Poppler\ __poppler folder__ \bin" to your SYSTEM PATH environment variable.
 
 1. Restart PC(if necessary).
 
### For single file 

```Python
from pdf2image import convert_from_path
pages = convert_from_path("pdf file", 300)

for page in pages:
    page.save('out.jpg', 'JPEG')
 ```
:red_circle: _Here 'pdf file' is relative path._

#### Reference :https://stackoverflow.com/questions/46184239/python-extract-a-page-from-a-pdf-as-a-jpeg
