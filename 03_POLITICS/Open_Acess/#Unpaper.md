<h3>Unpaper - Built-in</h3>

<h5>Unpaper built-in - OCRFeeder (GUI)</h5>

https://wiki.gnome.org/Apps/OCRFeeder<br>

<pre><code><span>$</span> sudo apt install -y ocrfeeder</code></pre>

<p>Tools -> Unpaper</p>

<h5>Unpaper built-in - OcrmOCRmyPDF (CLI)</h5>

https://ocrmypdf.readthedocs.io<br>

<pre><code><span>$</span> sudo apt install -y ocrmypdf</code></pre>
<pre><code><span>$</span> ocrmypdf --clean </code></pre>
<pre><code><span>$</span> ocrmypdf --clean-final </code></pre>
<pre><code><span>$</span> ocrmypdf --remove-background </code></pre>

<p>Note that <code>--clean-final</code> and <code>--remove-background</code> may leave undesirable visual artifacts in some images where their algorithms have shortcomings. Files should be visually reviewed after using these options.</p>

<p><code>--remove-background</code> attempts to detect and remove a noisy background from grayscale or color images. Monochrome images are ignored. This should not be used on documents that contain color photos as it may remove them.</p>

<p><code>--clean</code> uses <code>unpaper</code> to clean up pages before OCR, but does not alter the final output. This makes it less likely that OCR will try to find text in background noise.</p>

<p><code>--clean-final</code> uses <code>unpaper</code> to clean up pages before OCR and inserts the page into the final output. You will want to review each page to ensure that unpaper did not remove something important.</p>

<p>--clean uses <code>unpaper</code> to clean up pages before OCR, but does not alter the final output. This makes it less likely that OCR will try to find text in background noise.</p>

<h3>Unpaper - A post-processing tool for scanned sheets of paper</h3>

https://github.com/unpaper/unpaper<br>
https://github.com/unpaper/unpaper/blob/main/doc/basic-concepts.md<br>
https://github.com/unpaper/unpaper/blob/main/doc/image-processing.md<br>
https://diybookscanner.org<br>
https://diybookscanner.org/forum<br>
https://scantips.com<br>
https://mesonbuild.com/Quick-guide.html#compiling-a-meson-project<br>
https://gallium.readthedocs.io/en/latest/meson.html<br>
https://imagemagick.org/script/formats.php<br>
https://netpbm.sourceforge.net/doc/pnm.html<br>

<h4>SANE - Lists of linux supported scanners firmware</h4>

http://www.sane-project.org<br>
http://www.sane-project.org/sane-supported-devices.html<br>

<p>The output format of Unpaper is restricted to the PNM family of formats, and conversions to other formats need to happen with tools such as pnmtopng, pnmtotiff or pnmtojpeg. Alternatively you can use the convert tool from ImageMagick.</p>

<p>PNM is a family of formats supporting portable bitmaps (.pbm) , graymaps (.pgm), and pixmaps (.ppm). There is no file format associated with pnm itself. If PNM is used as the output format specifier, then ImageMagick automagically selects the most appropriate format to represent the image. The default is to write the binary version of the formats. Use -compress none to write the ASCII version of the formats. On some platforms, ImageMagick automagically processes a PNM image, called image.pnm.gz is automagically uncompressed.</p>

<p>Unpaper uses the Meson Build system, which can be installed using Python's package manage (pip3 or pip), the only hard dependency of Unpaper is ffmpeg, </p>

<pre>
• Commands, python and ffmpeg installation using package manager
$ sudo apt install python3 &&
sudo apt install python3-pip &&
sudo apt install python3-setuptools &&
sudo apt install python3-wheel &&
sudo apt install ninja-build &&
sudo apt install python3-mesonpy &&
sudo apt install python3-sphinx &&
sudo apt install python3-pytest &&
sudo apt install python3-pil &&
sudo apt install cmake &&
sudo apt install pkg-config &&
sudo apt install libavformat-dev &&
sudo apt install ffmpeg &&
sudo apt install git 
<pre>

<h5>Error: libavformat-dev</h5>

Install other depedencies<br>

<pre><code><span>$</span> sudo apt install libsdl2-dev libavcodec-dev libavdevice-dev libavformat-dev libavutil-dev libswresample-dev libusb-1.0-0 libusb-1.0-0-dev</code>


<p>Basic configuration. The most common use case of Meson is compiling code on a code base you are working on.</p>

<pre>
• Compiling Unpaper with Meson project
$ git clone https://github.com/unpaper/unpaper
$ cd unpaper
$ CFLAGS="-march=native" meson --buildtype=debugoptimized builddir -Db_lto=true
$ meson compile -C builddir
</pre>

<em>Warning: Before making modifications to files, create backup copies.</em>

<p>File formats</p>

https://github.com/unpaper/unpaper/blob/main/doc/file-formats.md<br>

$ sudo apt install imagemagick

<pre>
• Commands to convert .png in .pbm
$ cd ~/Folder
$ find . -name "*.png" -exec mogrify -monitor -format pbm {} \;
</pre>

<pre>
• Commands to convert .pdf in .pbm
$ convert -monitor input.pdf +repage -quality 100 output%03d.pbm
$ convert -monitor "*.pdf" +repage -path /livros output%03d.pbm
$ find . -name "*.pdf" -exec convert *.pdf output%03d.pbm
</pre>

<p>Imagemagick Repage</p>
https://imagemagick.org/Usage/crop/#crop_repage

<p>You can use the special "+repage" operator to reset the page canvas and position to match the actual cropped image.</p>

<p>* -repage: adjust the canvas and offset information of the image.</p>
<p>* +repage: offset may need to be removed using +repage, to remove if it is unwanted.</p>

<pre>
• Commands to convert multiple .pbm in .pdf
$ convert -monitor *.png +adjoin output.pdf
$ convert -monitor *.pbm output.pdf
$ find . -name "*.pbm" -exec convert -units PixelsPerInch *.pbm -density 96 output.pdf
</pre>

<p>Imagemagick Adjoin</p>

https://imagemagick.org/script/command-line-options.php#adjoin</p>

<p>Join images into a single multi-image file.</p>

<p>* -adjoin: join images into a single multi-image file</p>
<p>* +adjoin: to force each image to be written to separate files, whether or not the file format allows multiple images per file (for example, GIF, MIFF, and TIFF).</p>

Alternative - Combining pictures into PDF file<br>

ttps://gitlab.mister-muffin.de/josch/img2pdf<br>

<pre>
$ img2pdf --pagesize A4 img*.png
$ img2pdf --pagesize A4 img*.png | ocrmypdf - myinput.pdf
$ img2pdf --imgsize 300dpix300dpi -i *.jp2 -o output.pdf 
</pre>

<pre>
• Commands to reduce .pdf size
$ convert -monitor +repage -density 200 -quality 60 -compress jpeg input.pdf output.pdf
$ convert -monitor +repage input.pdf -resample 85% output.pdf
$ convert -monitor +repage scan*.jpg -colorspace gray -resample 100% "input.pdf"
$ convert -monitor +repage -compress Zip -density 200 input.pdf output.pdf
</pre>

-----------------------------------------------------------

<h5>Error: mogrify-im6.q16: attempt to perform an operation not allowed by the security policy `PDF' @ error/constitute.c/IsCoderAuthorized/426</h5>

<pre>
• Policy edit
$ sudo sed -i '/disable ghostscript format types/,+6d' /etc/ImageMagick-6/policy.xml

• Alternatively uncomment 
$ sudo nano /etc/ImageMagick-6/policy.xml

<policy domain="coder" rights="none" pattern="{PS,PS2,PS3,EPS,PDF,XPS}" />

• Alternatively remove this whole following section 
$ sudo nano /etc/ImageMagick-6/policy.xml

<!-- disable ghostscript format types -->
<policy domain="coder" rights="none" pattern="PS" />
<policy domain="coder" rights="none" pattern="PS2" />
<policy domain="coder" rights="none" pattern="PS3" />
<policy domain="coder" rights="none" pattern="EPS" />
<policy domain="coder" rights="none" pattern="PDF" />
<policy domain="coder" rights="none" pattern="XPS" />

</pre>

-----------------------------------------------------------

-----------------------------------------------------------

<h5>Error: convert-im6.q16: cache resources exhausted</h5>

<pre>
• Increase the available memoryfile
$ sudo nano /etc/ImageMagick-6/policy.xml

<policy domain="resource" name="memory" value="3GB"/>
<policy domain="resource" name="disk" value="3GB"/>

• Alternatively use
$ convert -limit memory 1GiB -limit disk 1GiB *.png new.pdf
</pre>

-----------------------------------------------------------

<p>Renaming in numbered order</p>

<pre>
• Renamer
$ sudo apt install rename
• Commands to rename to numbered order
$ cd /bookfolder
• Test the output before
$ rename -n 's/.+/our $i; sprintf("input%03d.png", 1+$i++)/e' *
• Apply the change
$ rename 's/.+/our $i; sprintf("input%03d.png", 1+$i++)/e' *
</pre>

<p>Unpaper - Basic usage</p>

https://github.com/unpaper/unpaper/blob/main/doc/basic-concepts.md<br>

<p>Use case: two pages per sheet, "open book" format where the input image-file already contains two scanned pages in a double-page layout</p>

<img src="https://github.com/RENANZG/My-Debian-GNU-Linux/blob/main/.data/multiple-output-files.png" title="Multiple Output Files" alt="Multiple Output Files" />

<p>Process multiple files using a wildcard of the form %0nd, e.g. input%03d.pbm and output%03d.pbm. It will successively read images from files input001.pbm, input002.pbm, input003.pbm etc., and write output to the files output001.pbm, output002.pbm, output003.pbm etc., until no more input image-files with the current index number are available. Wildcards in filenames like "%03d" will get replaced with strings in the sequence 001, 002, 003 etc.</p>

<pre>
• Commands for double-page layout
$ unpaper --layout double input%03d.pbm output%03d.pbm
$ unpaper --layout double input%03d.pbm --output-pages 2 output%03d.pbm
</pre>

<p>Use case: combine single-page image-files onto a double-page layout sheet</p>

<img src="https://github.com/RENANZG/My-Debian-GNU-Linux/blob/main/.data/multiple-input-files.png" title="Multiple Input Files" alt="Multiple Input Files" />

<pre>
• Commands for single-page onto a double-page layout sheet
$ unpaper --no-processing --input-pages 2 singlepage%03d.pgm output%03d.pgm
</pre>

<p>Image processing</p>

https://github.com/unpaper/unpaper/blob/main/doc/image-processing.md<br>

<pre>
• Commands
$ unpaper 
• Commands
$ 
</pre>

<h5>Processing of multipage with ImageMagick</h5>

<p>Command line processing of multipage book-type scanned documents with ImageMagick.</p>

https://edison23.net/blog/posts/crop-and-split-book-scan-in-3-commands<br>
http://www.imagemagick.org/script/command-line-processing.php#geometry<br>

<pre><code><span>$</span> sudo apt install imagemagick</code></pre>

<p>*Note that <code>convert</code> is part of ImageMagick package.</p>

<p>How to make a clean PDF with one page per sheet. The quality and quantity of additional work depends on how carefully you digitized the book.</p>

<pre>
• Command all-in-one
$ convert -monitor -density 300 orig-scan.pdf pages.png convert `ls pages-*.png` -crop 3704x1852+160+20 +repage -crop 50%x100% pages-split.png convert `ls pages-split*` -page 100%x100% result.pdf
</pre>

<pre>
• Commands
• Convert PDF to images in ordered sequence
$ convert -density 300 orig-scan.pdf pages.png
$ convert -density 300 orig-scan.pdf[0-9] pages.png
• Batch cropping and batch splitting the pages (*before, test the resullt)
$ convert `ls pages-*.png` -crop 3704x1852+160+20 +repage -crop 50%x100% pages-split.png
• Recombining all the single pages back to PDF
$ convert `ls pages-split*` -page 100%x100% result.pdf
• Commands
$ 
</pre>
