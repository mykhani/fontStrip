How to strip a larger font file for embedded systems
====================================================
The Google OTF font files are the best resources for adding support
for languages like Chinese, Japanese and Korean. However, the size
of single OTF file could well exceed 10MB, making it unsuitable for
resource constrained embedded applications. Therefore, follow the below
steps to strip a single OTF font file into a stripped version containing
only glyphs actually used by the application. For this, you need to 
provide a text file containing all the strings used inside the application.

Steps
=====
1. Install uni2ascii tool.
```
$ apt-get install uni2ascii
``` 

2. Install the fonttools: https://github.com/fonttools/fonttools
```
$ pip install fonttools
```

3. Gather the application text resources file.

4. Convert the text resources files into ascii using the below command.
```
$ uni2ascii -a P -p text-resource-file > text-resource-file-in-unicode
```

5. Finally generate the stripped font file using the base font file and the unicode-converted text resource file.
```
$ pyftsubset base.otf --output-file=stripped.otf --unicodes-file=text-resource-file-in-unicode
```
