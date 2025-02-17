<div>
<h2>Post-processing Documents in Debian GNU/Linux</h2>

<div>
<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Image Convert</summary>
<br>

<h4>Image Convert</h4>

<h5>Convert image with ImageMagick</h5>

https://imagemagick.org/script/formats.php<br>
https://imagemagick.org/script/mogrify.php<br>
https://imagemagick.org/script/command-line-tools.php<br>
https://cvedetails.com/vendor/1749/Imagemagick.html<br>

<pre><code><span>$ </span>sudo apt install imagemagick</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install imagemagick')">Copy</button>

<p>
<small>*Note that <code>mogrify</code> is part of ImageMagick package. The command
<code>convert</code> or <code>magick convert</code> is an old "legacy" program,
provided for compatabilty only, don't use it for new work. Instead, use just
<code>magick mogrify</code> or just <code>mogrify</code> .</small>
</p>

<pre>
• One-liner commands
$ mogrify -format png *.jpg
$ mogrify -format png *.jpeg
$ mogrify -format png *.webp
$ mogrify -format png *.svg
$ mogrify -format png *.avif
$ mogrify -format png *.gif
• Batch processing commands
$ cd ~/Donwloads
$ find . -name "*.jpg" -exec mogrify -monitor -format png {} \;
$ find . -name "*.jpeg" -exec mogrify -monitor -format png {} ;
$ find . -name "*.webp" -exec mogrify -monitor -format png {} \;
$ find . -name "*.svg" -exec mogrify -monitor -format png {} \;
$ find . -name "*.avif" -exec mogrify -monitor -format png {} \;
$ find . -name "*.gif" -exec mogrify -monitor -format png {} \;</pre>

<h5>Rotate image with ImageMagick</h5>

<a href="https://www.fmwconcepts.com/imagemagick/unrotate/index.php">UNROTATE</a>
<a href="https://www.fmwconcepts.com/imagemagick/unrotate2/index.php">UNROTATE2</a>
<a href="https://www.fmwconcepts.com/imagemagick/unrotate3/index.php">UNROTATE3</a>

<pre><code><span>$ </span>sudo apt install imagemagick</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install imagemagick')">Copy</button>

<pre>
• Commands
$ mogrify -monitor -rotate -90 *.png
</pre>

<h5>Deskew text-image with ImageMagick</h5>

<a href="https://www.fmwconcepts.com/imagemagick/textdeskew/index.php">TEXTDESKEW</a>

<pre>
• Commands
$ magick [image_source] -set option:angle "%[minimum-bounding-box:unrotate]" -background white -rotate "%[angle]" [image_target]
$ magick input.jpeg -deskew 60% output.jpg
</pre>

<h4>Unpaper</h4>

<h5>Unpaper built-in - OCRFeeder (GUI)</h5>

https://wiki.gnome.org/Apps/OCRFeeder<br>

<pre><code><span>$ </span>sudo apt install -y ocrfeeder</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y ocrfeeder')">Copy</button>

<p>Tools -> Unpaper</p>
<h5>Unpaper built-in - OCRmyPDF (CLI)</h5>

https://ocrmypdf.readthedocs.io<br>
https://ocrmypdf.readthedocs.io/en/latest/cookbook.html<br>

<pre><code><span>$ </span>sudo apt install -y ocrmypdf</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y ocrmypdf')">Copy</button>
<pre><code><span>$ </span>ocrmypdf --clean</code></pre>
<button onclick="navigator.clipboard.writeText('ocrmypdf --clean')">Copy</button>
<pre><code><span>$ </span>ocrmypdf --clean-final</code></pre>
<button onclick="navigator.clipboard.writeText('ocrmypdf --clean-final')">Copy</button>
<pre><code><span>$ </span>ocrmypdf --remove-background</code></pre>
<button onclick="navigator.clipboard.writeText('ocrmypdf --remove-background')">Copy</button>

<p>
Note that <code>--clean-final</code> and <code>--remove-background</code> may
leave undesirable visual artifacts in some images where their algorithms have
shortcomings. Files should be visually reviewed after using these options.
</p>

<p>
<code>--remove-background</code> attempts to detect and remove a noisy
background from grayscale or color images. Monochrome images are ignored. This
should not be used on documents that contain color photos as it may remove them.
</p>

<p>
<code>--clean</code> uses <code>unpaper</code> to clean up pages before OCR, but
does not alter the final output. This makes it less likely that OCR will try to
find text in background noise.
</p>

<p>
<code>--clean-final</code> uses <code>unpaper</code> to clean up pages before
OCR and inserts the page into the final output. You will want to review each
page to ensure that unpaper did not remove something important.
</p>

<p>
--clean uses <code>unpaper</code> to clean up pages before OCR, but does not
alter the final output. This makes it less likely that OCR will try to find text
in background noise.
</p>
<h5>Convert with webp (dwebp)</h5>

<pre><code><span>$ </span>sudo apt install webp</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install webp')">Copy</button>

<pre>
  Commands for webp files 
• How to convert .webp to .png #It's a command-line interface
$ dwebp -v input.webp -o ~/output.png
$ dwebp -v -resize width x height input.webp -o ~/output.png *If either (but not both) of the width or height parameters is 0, the value will be calculated preserving the aspect-ratio.
</pre>

<pre>
  Commands for webp files in batch 
$ for file in *.webp ; do dwebp "$file" -o "${file%.*}.png" ; done 
• Testing alternatives 
$ find . -name "*.webp" -exec dwebp {} -o "${file%.*}.png" \; 
$ find . -type f -name "*.webp" -exec dwebp {} -o *.png 
$ sudo apt install parallel 
$ parallel dwebp {} -o *.png 
$ find . -name "*.webp" -print0 | parallel --progress -0 dwebp {} -o *.png
$ for x in 'ls -1 *.jpg'; do dwebp {} -o ${x%.*}.png ; done 
$ for x in 'find . -name "*.webp"'; do dwebp {} -o ${x%.*}.png ; done
</pre>

<br>
</details>

<!-- ############################## -->

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF Convert</summary>
<br>

<h4>Libre Office (Headless)</h4>

<p>
See
<a
href="https://help.libreoffice.org/latest/en-US/text/shared/guide/convertfilters.html">LibreOffice documentation</a>
for more information.
</p>

<pre><code><span>$ </span> sudo apt install -y libreoffice</code></pre>

<!-- ##### -->

<h5>Commands for LibreOffice Headless</h5>

<dl>
<dt>Syntax:</dt>
<dd>
<pre><code><span>$ </span> soffice --convert-to OutputFileExtension[:OutputFilterName[:OutputFilterParams[,param]]] [--outdir output_dir]</code></pre>
</dd>
<dt>To convert a DOCX file to PDF:</dt>
<dd>
<pre><code><span>$ </span> soffice --headless --convert-to pdf:writer_pdf_Export --outdir /home/user *.docx</code></pre>
</dd>
<dt>To convert a ODT file to PDF:</dt>
<dd>
<pre><code><span>$ </span> soffice --headless --convert-to pdf:writer_pdf_Export --outdir /home/user *.odt</code></pre>
</dd>
</dl>

<!-- ##### -->

<h5>Output as PDF</h5>

<p>
To control which LibreOffice component generates PDF output, you can use these
variants:
</p>

<pre>
--convert-to pdf:writer_pdf_Export 
--convert-to pdf:calc_pdf_Export 
--convert-to pdf:draw_pdf_Export 
--convert-to pdf:impress_pdf_Export 
--convert-to pdf:writer_web_pdf_Export
</pre>

<!-- ########## -->

<h4>Pandoc</h4>

<p>
Pandoc - a universal document converter
<a href="https://pandoc.org/">https://pandoc.org/</a>.
</p>

<pre><code><span>$ </span>sudo apt install -y pandoc</code></pre>

<!-- ##### -->

<h5>Commands for Pandoc</h5>

<ul>
<li>
Convert ODT to DOCX: <code>$ pandoc -o document.odt document.docx</code>
</li>
<li>
Convert DOCX to PDF: <code>$ pandoc -s document.docx -o document.pdf</code>
</li>
</ul>

<br>
</details>

<!-- ############################## -->

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF Optimizers</summary>
<br>

<h4>ImageMagick (GUI or CLI)</h4>

<a href="https://imagemagick.org/Usage/crop">https://imagemagick.org/Usage/crop</a><br>
<a href="https://imagemagick.org/Usage/crop/#crop_repage">https://imagemagick.org/Usage/crop/#crop_repage</a><br>
<a href="https://cvedetails.com/vendor/1749/Imagemagick.html">https://cvedetails.com/vendor/1749/Imagemagick.html</a><br>

<pre><code><span>$ </span>sudo apt install imagemagick</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install imagemagick')">Copy</button>

<p>
<small>*Note that <code>mogrify</code> is part of ImageMagick package. The command
<code>convert</code> or <code>magick convert</code> is an old "legacy" program,
provided for compatabilty only, don't use it for new work. Instead, use just
<code>magick mogrify</code> or just <code>mogrify</code>.</small>
</p>

<h5>Commands to crop .pdf</h5>

<pre><code><span>$ </span>mogrify -monitor 'ls input-*.png' -crop 3704x1852+160+20 output.png</code></pre>

<pre><code><span>$ </span>mogrify -monitor -crop 1000x1350+20+145 +repage -path cropped *.png</code></pre>

<p>Monitor progress: <code>-monitor</code></p>

<p>Print detailed information about the image: <code>-verbose</code></p>

<h5>Commands to reduce .pdf size</h5>

<pre><code><span>$ </span>mogrify -monitor -density 300x300 -quality 100 input.pdf output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor -density 200x200 -quality 60 -compress jpeg input.pdf output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor -density 150x150 -quality 70 -compress jpeg -resize 15% input.pdf output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor -density 150x150 -compress Zip input.pdf output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor -density 80 -page a4 input.pdf output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor input.pdf -resample 85% output.pdf</code></pre>

<pre><code><span>$ </span>mogrify -monitor *.png -colorspace gray -resample 100% "input.pdf"
</code></pre>

<h5>• Commands to scanned books</h5>

<pre><code><span>$ </span>mogrify -normalize -density 300 -depth 8 *.png</code></pre>

<pre><code><span>$ </span>mogrify -normalize -density 300 -depth 8 -crop 50%x100% +repage *.png</code></pre>

<pre><code><span>$ </span>mogrify -monochrome -normalize -density 300 *.png</code></pre>

<p>
<code>-normalize</code>: increase the contrast in an image by stretching the
range of intensity values.
</p>

<p><code>-depth</code>: the number of bits per channel for each pixel.</p>

<p><code>-monochrome</code>: transform the image to black and white.</p>

<p>pdfCropMargins - Python</p>

<a href="https://pypi.org/project/pdfCropMargins">https://pypi.org/project/pdfCropMargins</a><br>

<pre>
$ pip install "pdfCropMargins" --upgrade
$ pdf-crop-margins -v -p 0 -a -6 input.pdf
</code></pre>

<h4>Ghostscript</h4>

<a href="https://ghostscript.com">https://ghostscript.com</a><br>
<a href="https://cvedetails.com/vendor/10846/Artifex.html">https://cvedetails.com/vendor/10846/Artifex.html</a><br>

<pre><code><span>$ </span>sudo apt install -y ghostscript</code></pre>

<h5>Commands to optimize PDF</h5>

<p>Rewrites the PDF, sometimes cleaning up unwanted elements.</p>

<pre><code>
gs -o output.pdf -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress input.pdf
</code></pre>

<h5>Convert PDF - Reduce size of scanned book</h5>

<pre><code>
gs -dNOPAUSE -dBATCH -dQUIET \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/screen \
-sOutputFile=output.pdf \
  input.pdf
</code></pre>

<pre><code>
gs -dNOPAUSE -dBATCH -dQUIET \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/printer \
-sOutputFile=output.pdf \
input.pdf
</code></pre>

<pre><code>
gs -dNOPAUSE -dBATCH -dQUIET \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/prepress \
-dDetectDuplicateImages \
-dCompressFonts=true -r150 \
-sOutputFile=output.pdf \
input.pdf
</code></pre>

<pre><code>
gs -dNOPAUSE -dBATCH -dQUIET \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/prepress \
-dDetectDuplicateImages \
-dCompressFonts=true -r300 \
-sOutputFile=output.pdf \
input.pdf
</code></pre>

<h5>Convert PDF - Reduce size of Acrobat PDF</h5>

<p><small>*Test results with comp. 1.3 and 1.4 .</small></p>

<pre><code>
gs -dNOPAUSE -dBATCH -dSAFER \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/ebook \
-dEmbedAllFonts=true \
-dSubsetFonts=true \
-dColorImageDownsampleType=/Bicubic \
-dColorImageResolution=96 \
-dGrayImageDownsampleType=/Bicubic \
-dGrayImageResolution=96 \
-dMonoImageDownsampleType=/Bicubic \
-dMonoImageResolution=96 \
-sOutputFile=output.pdf input.pdf
</code></pre>

<pre><code>
gs -dNOPAUSE -dBATCH -dSAFER \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.3 -dPDFSETTINGS=/screen \
-dEmbedAllFonts=true \
-dSubsetFonts=true \
-dColorImageDownsampleType=/Bicubic \
-dColorImageResolution=144 \
-dGrayImageDownsampleType=/Bicubic \
-dGrayImageResolution=144 -dMonoImageDownsampleType=/Bicubic \
-dMonoImageResolution=144 \
-sOutputFile=output.pdf input.pdf
</code></pre>

<pre>
• Batch combine tips 
$ cd /folder 
$ find . -name '*.pdf' -execgs -o -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress -sOutputFile=../output.pdf {} +
</pre>

<pre>
• Batch process all pdfs one by one renaming the output 
$ cd /folder 
$ find . -name '*.pdf' -exec sh -c ' for pdf; do output="${pdf%.pdf}-processed.pdf"gs -dNOPAUSE -dBATCH -dSAFER \
-sDEVICE=pdfwrite \
-dCompatibilityLevel=1.4 \
-dPDFSETTINGS=/screen \
-dEmbedAllFonts=true \
-dSubsetFonts=true \
-dColorImageDownsampleType=/Bicubic \
-dColorImageResolution=144 \
-dGrayImageDownsampleType=/Bicubic \
-dGrayImageResolution=144 -dMonoImageDownsampleType=/Bicubic \
-dMonoImageResolution=144 \
-sOutputFile="$output" "$pdf" done ' sh {} +
</pre>

<pre>
• Name tips 
-sOutputFile=ABC-%d.png produces 'ABC-1.png', ... , 'ABC-10.png', .. 
-sOutputFile=ABC-%03d.pgm produces 'ABC-001.pgm', ... , 'ABC-010.pgm', ... 
-sOutputFile=ABC_p%04d.tiff produces 'ABC_p0001.tiff', ... , 'ABC_p0510.tiff', ... , 'ABC_p5238.tiff'
</pre>

<p><small>
• References -dPDFSETTINGS=/screen - Low quality and small size at 72dpi.
-dPDFSETTINGS=/ebook - Slightly better quality but also a larger file size at
150dpi. -dPDFSETTINGS=/prepress - High quality and large size at 300 dpi.
-dPDFSETTINGS=/default - System chooses the best output, which can create larger
PDF files.
</small></p>

<pre>
  Commands for ebook-convert
• How to convert .epub to .pdf 
$ sudo apt install calibre
$ ebook-convert input  .epub output.pdf
$ ebook-convert input.epub output.pdf --enable-heuristics
$ find ./ -iname "*pdf" -type f | while read f; do echo -e "\e[1mConverting file $f \e[0m" ; ebook-convert "$f" "${f%.pdf}.epub" --enable-heuristics ; done
</pre>

<p>*Ref.:<a href="https://manpages.debian.org/bookworm/calibre/ebook-convert.1.en.html">https://manpages.debian.org/bookworm/calibre/ebook-convert.1.en.html</a></p>

<p>*Utility.: <a href="https://convertfiles.com">https://convertfiles.com</a></p>

<pre>
  Commands for ps2pdf
• How to convert .ps to .pdf 
$ sudo apt install ps2pdf
$ ps2pdf -dPDFSETTINGS=/ebook input.pdf output.pdf
</code></pre>

<p>*LibreOffice Draw: DPI of 100 and JPEG compression of 80%.</p>

<p>*Try:</p>

<pre>
$ ps2pdf input.pdf output.pdf
</code></pre>

<br>
</details>

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF Suites</summary>
<br>

<h4>PDF Reader</h4>

<pre><code><span>$ </span>sudo apt install -y okular</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y okular')">Copy</button>

<pre><code><span>$ </span>sudo apt install -y okular-extra-backends</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y okular-extra-backends')">Copy</button>

<!-- ########## -->

<h4>PDF Editor</h4>

<p>PDF Arranger (GUI)</p>

https://github.com/pdfarranger/pdfarranger<br>

<pre><code><span>$ </span>sudo apt install -y pdfarranger</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y pdfarranger')">Copy</button>

<p>
Manually Crop or Remove Pages: This tool is more for rearranging and cropping
pages, but it can also be useful for removing unwanted sections.
</p>

<!-- ########## -->

<h4>How to combine PDFs in CLI</h4>

<pre><code><span>$ </span>sudo apt install -y ghostscript</code></pre>

<pre>
• Command to combine
$gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -sOutputFile=combined.pdf file1.pdf file2.pdf
• Output in low resolution
$gs -dBATCH -dNOPAUSE -q -sDEVICE=pdfwrite -dPDFSETTINGS=/prepress -sOutputFile=merged.pdf mine1.pdf mine2.pdf
</code></pre>

<!-- ########## -->

<!-- ########## -->

<br>
</details>

<!-- ############################## -->

<!-- ############################## -->

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF Crop and Split</summary>
<br>

<h5>Krop (GUI)</h5>

https://arminstraub.com/software/krop<br>

<p>
Krop is designed to adjust which parts of a PDF are displayed by changing the
crop box of the PDF. This means the original content is still in the file and
can be revealed or accessed using a PDF editor or viewer that ignores the crop
box. Krop is not suited for censoring a PDF document or decreasing the size of a
PDF file.
</p>

<pre><code><span>$ </span>sudo apt install -y krop</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y krop')">Copy</button>

<pre>
• To automatically undo 4 pages print onto a single page:
$ krop --go --grid=2x2 input.pdf
• To trim each of these pages:
$ krop --go --grid=2x2 --trim --trim-use=all input.pdf
• Others krop --grid=2x1 --initialpage=3 --exceptions=1 --trim-use=all --trim ~/input.pdf
</code></pre>

<p>
<small>
--trim: Trims whitespace around the content. --trim-use=all: Uses all pages to
determine the trim area, ensuring a consistent crop.
</small>
</p>

<!-- ##### -->

<h5>pdfcrop (texlive-extra-utils)</h5>

<pre><code><span>$ </span>sudo apt install -y texlive-extra-utils</code></pre>

<p>
Adjust the margins, effectively trimming the PDF. pdfcrop is a tool that uses
Ghostscript to crop whitespace or specified margins from a PDF.
</p>

<pre>
• Command
$ pdfcrop input.pdf output.pdf
$ pdfcrop --margins '-10 -10 -10 -10' input.pdf output.pdf
$ pdfcrop --margins '0 0 0 -50' input.pdf output.pdf
</code></pre>

<!-- ##### -->

<h5><a href="https://github.com/rrthomas/pdfjam">pdfjam</a></h5>

<pre><code><span>$ </span>sudo apt install -y pdfjam</code></pre>

<pre>
• Commands
$ pdfjam --twoside --offset '0cm 0cm' --paper a4paper cropped.pdf --outfile final.pdf
</code></pre>

<!-- ##### -->

<h5>pdftk</h5>

<pre><code><span>$ </span>sudo apt install -y pdftk</code></pre>

<pre>
• Command to remove page 4
$ pdftk input.pdf cat 1-3 5-end output output.pdf
• Command 
$ pdftk input.pdf cat 1-endeast output rotated.pdf
</code></pre>

<br>
</details>

<!-- ############################## -->

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF OCR</summary>
<br>

<h4>• PDF OCR - Optical Character Recognition</h4>

<h5>OCRFeeder (GUI)</h5>

https://wiki.gnome.org/Apps/OCRFeeder<br>

<pre><code><span>$ </span>sudo apt install -y ocrfeeder</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y ocrfeeder')">Copy</button>

<p><b>*Unpaper</b></p>

<h5>Cuneiform (CLI)</h5>

https://packages.debian.org/bookworm/cuneiform<br>

<h5>OcrmOCRmyPDF (CLI)</h5>

https://ocrmypdf.readthedocs.io<br>

<pre><code><span>$ </span>sudo apt install -y ocrmypdf</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y ocrmypdf')">Copy</button>

<p>Also install the Tesseract OCR plugins for your desired language</p>

<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-eng</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-eng')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-deu</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-deu')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-fra</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-fra')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-spa</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-spa')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-por</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-por')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-rus</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-rus')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-ara</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-ara')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-chi-sim</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-chi-sim')">Copy</button>
<pre><code><span>$ </span>sudo apt install -y tesseract-ocr-chi-tra</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install -y tesseract-ocr-chi-tra')">Copy</button>

<h4>OCRmyPDF Commands and Settings</h4>

<h5>Basic commands</h5>

<ul>
<li>How to OCR a PDF</li>
<li>
<pre><code>$ ocrmypdf -v input.pdf output.pdf</code></pre>
</li>
<li>
<pre><code>$ ocrmypdf -v --language eng input.pdf output.pdf</code></pre>
</li>
<li>
<pre><code>$ ocrmypdf -v --language eng+deu input.pdf output.pdf</code></pre>
</li>
<li>
<pre><code>$ ocrmypdf -v --language eng+spa input.pdf output.pdf</code></pre>
</li>
<li>
<pre><code>$ ocrmypdf -v --language por+deu input.pdf output.pdf</code></pre>
</li>
</ul>

<ul>
<li>To modify a file in the same place</li>
<li>$ ocrmypdf -v ~/input.pdf ~/input.pdf</li>
</ul>

<ul>
<li>To skip text</li>
<li>$ ocrmypdf -v --skip-text input.pdf output.pdf</li>
</ul>

<ul>
<li>To redo OCR</li>
<li>$ ocrmypdf -v --redo-ocr input.pdf output.pdf</li>
</ul>

<h3>Compression settings</h3>

<ul>
<li>
$ ocrmypdf -v --pdfa-image-compression=jpeg --language=por+deu input.pdf
output.pdf
</li>
<li>
$ ocrmypdf -v --pdfa-image-compression=lossless --language=por+deu input.pdf
output.pdf
</li>
<li>$ ocrmypdf -v --output-type=pdf --language por+deu input.pdf output.pdf</li>
</ul>

<h5>OcrmOCRmyPDF - Image processing</h5>

<ul>
<li>$ ocrmypdf -v --clean --language=por+deu input.pdf output.pdf</li>
<li>$ ocrmypdf -v --clean-final --language=por+deu input.pdf output.pdf</li>
<li>
$ ocrmypdf -v --remove-background --language=por+deu input.pdf output.pdf
</li>
</ul>

<h5>Warning</h5>

<p>
In many cases image processing will rasterize PDF pages as images, potentially
losing quality. We caution against using ImageMagick or Ghostscript to convert
images to PDF, since they may transcode images or produce downsampled images,
sometimes without warning.
</p>

<p>
OCRmyPDF perform some image processing on each page of a PDF, if desired. The
same processing is applied to each page. It is suggested that the user review
files after image processing as these commands might remove desirable content,
especially from poor quality scans.
</p>

<p>
Note that <code>--clean-final</code> and <code>--remove-background</code> may
leave undesirable visual artifacts in some images where their algorithms have
shortcomings. Files should be visually reviewed after using these options.
</p>

<p>
<code>--clean</code> uses <code>unpaper</code> to clean up pages before OCR, but
does not alter the final output. This makes it less likely that OCR will try to
find text in background noise.
</p>

<p>
<code>--clean-final</code> uses <code>unpaper</code> to clean up pages before
OCR and inserts the page into the final output. You will want to review each
page to ensure that unpaper did not remove something important.
</p>

<p>
<code>--remove-background</code> attempts to detect and remove a noisy
background from grayscale or color images. Monochrome images are ignored. This
should not be used on documents that contain color photos as it may remove them.
</p>

<h5>OcrmOCRmyPDF - PDF optimization</h5>

<ul>
<li>$ ocrmypdf -v --optimize=[0,1,2,3] input.pdf output.pdf</li>
</ul>

<p>
By default OCRmyPDF will attempt to perform lossless optimizations on the images
inside PDFs after OCR is complete. Optimization is performed even if no OCR text
is found.
</p>

<p>
The --optimize N (short form -O) argument controls optimization, where N ranges
from 0 to 3 inclusive, analogous to the optimization levels in the GCC compiler.
</p>

<p>
Optimization is improved when a JBIG2 encoder is available and when pngquant is
installed. If either of these components are missing, then some types of images
cannot be optimized.
</p>

<p>
The types of optimization available may expand over time. By default, OCRmyPDF
compresses data streams inside PDFs, and will change inefficient compression
modes to more modern versions. A program like qpdf can be used to change
encodings, e.g. to inspect the internals for a PDF.
</p>

<p>
<code>ocrmypdf --optimize 3 in.pdf out.pdf # Make it small Some users may consider
enabling lossy JBIG2. See: jbig2-lossy.</code>
</p>

<p>
Image processing and PDF/A conversion can also introduce lossy transformations
to your PDF images, even when <code>--optimize 1</code> is in use.
</p>

<h5>OcrmOCRmyPDF - PDF Rotation</h5>

<ul>
<li>$ ocrmypdf -v --deskew input.pdf output.pdf</li>
<li>$ ocrmypdf -v --rotate-pages input.pdf output.pdf</li>
<li>$ ocrmypdf -v --rotate-pages-threshold {0.0-2.0} input.pdf ou</li>
<li>$ ocrmypdf -v --deskew --rotate-pages --clean input.pdf output.pdf</li>
<li>$ ocrmypdf -v --deskew --skip-text input.pdf output.pdf</li>
<li>$ ocrmypdf -v --deskew --tesseract-timeout=0 input.pdf output.pdf</li>
</ul>

<p>
<code>--rotate-pages</code> attempts to determine the correct orientation for
each page and rotates the page if necessary.
</p>

<p>
<code>--deskew</code> will correct pages that were scanned at a skewed angle by
rotating them back into place.
</p>

<p>
<code>--clean</code> uses <code>unpaper</code> to clean up pages before OCR, but
does not alter the final output. This makes it less likely that OCR will try to
find text in background noise.
</p>

<p>
<code>--clean-final</code> uses <code>unpaper</code> to clean up pages before
OCR and inserts the page into the final output. You will want to review each
page to ensure that unpaper did not remove something important.
</p>

<br>
</details>

<!-- ############################## -->

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;PDF Others</summary>
<br>

<h4>PDF - Bookmarks Creation</h4>

https://github.com/SiddharthPant/booky<br>

<!-- ########## -->

<h4>PDF - Remove Annotations</h4>

<h5>Removing annotations at once in Okular</h5>

<p>
View a page that has an annotation, find them in the annotation side pane.
Right-click on the annotation icon in the document, and click Remove Annotation.
Then save the changes to a new document by clicking the menu button in the top
right, followed by Save As….
</p>

<pre>
  Commands for pdftocairo
$ pdftocairo -pdf "input.pdf" "output-with-flatten-annotations.pdf"
</pre>

<pre>
  Commands for qpdf
$ qpdf --flatten-annotations=all input.pdf output.pdf
</code></pre>

<p>*May apply some differences.</p>

<p>*May result in larger PDF.</p>

<!-- ########## -->

<h4>PDF - Remove Hiperlinks</h4>

<h5><a href="https://www.pdflabs.com/tools/pdftk-the-pdf-toolkit">PDFtk</a></h5>

<pre><code><span>$ </span>sudo apt install pdftk</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install pdftk')">Copy</button>

<p>Remove all interactive elements, including hyperlinks.</p>

<pre>
  pdftk input.pdf output cleaned.pdf
</code></pre>

<h5><a href="">qpdf</a></h5>

<pre><code><span>$ </span>sudo apt install qpdf</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install qpdf')">Copy</button>

<pre>
  
  qpdf --linearize --replace-input input.pdf cleaned.pdf
</code></pre>

<!-- ########## -->

<h4>PDF - Remove Metadata</h4>

<h5>Exiftool</h5>

<pre><code><span>$ </span>sudo apt install exiftool</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install exiftool')">Copy</button>

<p>
*Note: Exiftool PDF Tags "All metadata edits are reversible. While this would
normally be considered an advantage, it is a potential security problem because
old information is never actually deleted from the file. (However, after running
ExifTool the old information may be removed permanently using the "qpdf" utility
with this command: "qpdf --linearize in.pdf out.pdf".)"
</p>

<p>*Note: PDF Sanitize</p>

<pre>
  qpdf --sanitize input.pdf cleaned.pdf
  qpdf --linearize --sanitize input.pdf output.pdf
</code></pre>

<p>
--linearize: Does not remove any content but reorganizes it for optimized
loading, focuses on optimizing the file for faster web viewing. Useful when
hosting PDFs on websites to ensure users can start reading the document before
the entire file is downloaded.
</p>

<p>
--sanitize: Removes specific types of content like JavaScript and embedded
files, focuses on making the file safe by removing potentially harmful content.
Useful when sharing PDFs to ensure they do not contain any malicious content
that could harm the recipient's system.
</p>

<!-- ##### -->

<h5>Ghostscript</h5>

<pre><code><span>$ </span>sudo apt install gs</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install gs')">Copy</button>

<pre>
gs -dSAFER -dBATCH -dNOPAUSE -dNOCACHE -sDEVICE=pdfwrite -sOutputFile=cleaned.pdf -f input.pdf
gs -dSAFER -dBATCH -dNOPAUSE -sDEVICE=pdfwrite -dPrinted=false -sOutputFile=output.pdf input.pdf
</code></pre>

<!-- ########## -->

<h4>PDF - Read and Edit Metadata</h4>

<h5>pdfinfo</h5>

<pre><code><span>$ </span>sudo apt install poppler-utils</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install poppler-utils')">Copy</button>

<p>Poppler-utils package contains pdfinfo.</p>

<pre><code><span>$ </span>pdfinfo input.pdf</code></pre>
<button onclick="navigator.clipboard.writeText('pdfinfo input.pdf')">Copy</button>
<pre><code><span>$ </span>pdfinfo -meta input.pdf</code></pre>
<button onclick="navigator.clipboard.writeText('pdfinfo -meta input.pdf')">Copy</button>
<pre><code><span>$ </span>pdfinfo -js filename.pdf</code></pre>
<button onclick="navigator.clipboard.writeText('pdfinfo -js filename.pdf')">Copy</button>

<!-- ##### -->

<h5>Exiftool</h5>

<pre><code><span>$ </span>sudo apt install exiftool</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install exiftool')">Copy</button>

<pre>
  Commands for exiftool basic commands 
• Remove all metadata from all files possible inside a folder and all its ubfolders without backup (take care, might affect the colors) 
$ exiftool -v -all:all= -overwrite_original -r /path 
• Shows metadata: 
$ exiftool -a -Title input.pdf 
$ exiftool -G1 -a input.pdf 
$ exiftool -G1 -s 'input.pdf' | grep '\[PDF\]' 
$ exiftool -a -Model -ImageSize photo.jpg 
• Process all files of specified file type (case insensitive extension) 
$ exiftool -v -Model -ImageSize -ext jpg /path/to/files/ 
• Recursively process all jpg files under specified directory and sub-directory 
$ exiftool -v -r -Model -ImageSize -ext jpg /path/to/files/
</pre>

<pre>
• Editing PDF metadata from command line 
$ exiftool -Title=" " /
-Author=" " /
-Description=" " /
-Subject=" " /
-Date=" " /
-CreationDate=" " /
-Publisher=" " /
-ISBN=" " /
  input.pdf
</code></pre>

<p>
*To not create a backup in command-line the option is -overwrite_original.
</p>
<p>
*To not creat a backup in ExifToolGUI, there's menu "Options ">"Don 't backup
files when modifying".
</p>

<!-- ########## -->

<h4>PFD - Remove Watermark</h4>

<h5>pdftoppm</h5>

<pre><code><span>$ </span>sudo apt install pdftoppm</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install pdftoppm')">Copy</button>

<p>
If the watermark is at a fixed position on each page, you can use pdftoppm
command (part of Poppler utilities package) and convert command (from
ImageMagick package) to remove the watermark by cropping the pages.
</p>

<pre><code><span>$ </span>pdftoppm -png -cropbox input.pdf output</code></pre>
<button onclick="navigator.clipboard.writeText('pdftoppm -png -cropbox input.pdf output')">Copy</button>

<!-- ##### -->

<h5>Ghostscript</h5>

<pre><code><span>$ </span>sudo apt install gs</code></pre>
<button onclick="navigator.clipboard.writeText('sudo apt install gs')">Copy</button>

<pre><code>
gs -o output.pdf -sDEVICE=pdfwrite \
-c "[/Page 1 /View [/CropBox [0 0 612 792]] /Rect [0 0 612 792] /Action &lt;&lt; /Subtype /Hide /O 0&gt;&gt; /Subtype /Link /ANN pdfmark" \
-f input.pdf
</code></pre>

<p>
<small>This command tries to create a link annotation that hides content on the first
page. Adjust /Page 1 and coordinates [0 0 612 792] as necessary to target
specific areas or pages.</small>
</p>

<br>
</details>
</div>

<details>
<summary>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Renamers</summary>
<br>

<h4>Renamers</h4>

<h5>Online regex tools</h5>
• Dencode - https://dencode.com<br>
• Commonly Used Software Development Tools - https://ctool.dev<br>
• Text Fixer - https://textfixer.com<br>
• SS64 Syntax Utils - https://ss64.com<br>
• Tools4noobs - https://tools4noobs.com<br>
• Regex101 - https:// regex101.com<br>
<!-- ########## -->

<h5>File Naming Best Practices</h5>

<p>
You might consider including some of the following information in your file
names, but you can include any information that will allow you to distinguish
your files from one another.
</p>

<ul>
<li>Project or experiment name or acronym</li>
<li>Location/spatial coordinates</li>
<li>Researcher name/initials</li>
<li>Date or date range of experiment</li>
<li>Type of data</li>
<li>Conditions</li>
<li>Version number of file</li>
<li>Three-letter file extension for application-specific files</li>
</ul>

<p>
<small>Another good idea is to include in the directory a readme.txt file that
explains your naming format along with any abbreviations or codes you have
used.</small>
</p>

<p>Machine readable</p>

<ul>
<li>
Regular expression and globbing friendly
<ul>
<li>Avoid spaces, punctuation, accented characters, case sensitivity</li>
<li>Easy to compute on</li>
</ul>
</li>
<li>Deliberate use of delimiters</li>
</ul>
<p>Consider these additional tips as you develop a file naming scheme:</p>
<ul>
<li>
A good format for date designations is YYYYMMDD or YYMMDD. This format makes
sure all of your files stay in chronological order, even over the span of many
years.
</li>
<li>
Try not to make file names too long, since long file names do not work well with
all types of software.
</li>
<li>
Special characters such as
<code>&#126; &#64; &#35; &#36; &#37; &#94; &amp; &#42; &#40; &#41; &#96; &#59; &lt;
&gt; &#63; &#44; &#91; &#93; &#123; &#125; &#39; &quot; and &#124;
</code>
should be avoided.
</li>
<li>Illegal characters in Windows file names.</li>
<li>
When using a sequential numbering system, using leading zeros for clarity and to
make sure files sort in sequential order. For example, use "001, 002, ...010,
011 ... 100, 101, etc." instead of "1, 2, ...10, 11 ... 100, 101, etc."
</li>
<li>
Do not use spaces. Some software will not recognize file names with spaces, and
file names with spaces must be enclosed in quotes when using the command line.
Other options include:
<ul>
<li>Underscores, e.g. file_name.xxx</li>
<li>Dashes, e.g. file-name.xxx</li>
<li>No separation, e.g. filename.xxx</li>
<li>
Camel case, where the first letter of each section of text is capitalized, e.g.
FileName.xxx
</li>
</ul>
</li>
<li>
Periods can be used in file names&nbsp;but consider these points before doing so
and proceed cautiously:
<ul>
<li>Periods are used in regular expressions.</li>
<li>
Periods at the start of a file name are used to indicate configuration and/or
hidden files in a file directory.
</li>
<li>Periods are used to separate file names from file extensions.</li>
</ul>
</li>
</ul>

<!-- ########## -->

<h5>Special Symbols</h5>

<pre>
&#92;n is a symbol for new line &#92;t is a symbol for tab &#92;r is for 'return'</pre>

<p>
Note: \n or \t or \r are interpreted inside of &lt;pre&gt; text &lt;&#47;pre&gt;
</p>

<h5>Special HTML codes</h5>

<table>
<thead>
<tr>
<th>Char</th>
<th>
Numeric <br>
code
</th>
<th>
Named <br>
code
</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>&nbsp;</td>
<td>&amp;#09;</td>
<td>&nbsp;</td>
<td>horizontal tab</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&amp;#10;</td>
<td>&nbsp;</td>
<td>line feed</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&amp;#13;</td>
<td>&nbsp;</td>
<td>carriage return / enter</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&amp;#160;</td>
<td>&amp;nbsp;</td>
<td>on-breaking space</td>
</tr>
</tbody>
</table>

<!-- ########## -->

<h5>KRename</h5>

<pre><code><span>$ </span>sudo apt install krename
</code></pre>

<!-- ########## -->

<h5>GPRename</h5>

<pre><code><span>$ </span>sudo apt install gprename
</code></pre>

<!-- ########## -->

<h5>Case Styles</h5>

<pre>Camel case: camelCase</pre>

<pre>Pascal case: PascalCase</pre>

<pre>Kebab case: kebab-case</pre>

<pre>Snake case: snake_case</pre>

<pre>Dot case: dot.case</pre>

<pre>Title case: Title Case</pre>

<pre>Sentence case: Sentence case</pre>

<!-- ########## -->

<h4>Bash's built-in commands to rename (Debian/GNU Linux)</h4>

<h5>Safety check before irreversible batch processing rename</h5>

<pre><code>
$ for f in *; do echo mv "$f" "$(echo "$f" | tr 'A-Z' 'a-z')"; done
</code></pre>

<pre><code>
$ for f in *; do echo mv "$f" "$(echo "$f" | sed -e 's/\([A-Z]\)/-\L\1/g' | sed -e 's/^-//')"; done
</code></pre>

<!-- ########## -->

<h5>Note about uppercase and lowercase with one-liner command in Linux</h5>

<p>
Its impossible to rename a file in the same directory from uppercase to
lowercase with one-liner command due to the way Unix-like systems handle file
names. File systems on Unix-like systems (such as ext4, NTFS, etc.) are
typically case-sensitive. This means that FILENAME.txt and filename.txt are
treated as distinct files. However, you can achieve this by using a temporary
directory or by copying the file to a new name and then deleting the original.
</p>

<!-- ########## -->

<h5>Working with files instead of folders in one-liner command.</h5>

<p>
For example, if you have a file named CamelCase_Example.txt, running the command
will rename it to camel-case-example.txt.
</p>

<p>
Make sure to replace $1 with the actual filename if you're not passing it as an
argument to a script or command, and ensure you run the command in the directory
where the file is located.
</p>

<pre><code>
$ mv "$1" "$(echo "$1" | sed 's/\([a-z0-9]\)\([A-Z]\)/\1-\2/g' | tr '[:upper:]' '[:lower:]' | sed 's/_/-/g')"
</code></pre>

<pre><code>
$ mv "/dir/CamelCase_Example.txt" "$(echo "/dir/CamelCase_Example.txt" | sed 's/\([a-z0-9]\)\([A-Z]\)/\1-\2/g' | tr '[:upper:]' '[:lower:]' | sed 's/_/-/g')"
</code></pre>

<!-- ########## -->

<h4>One-liner built-in commands to rename</h4>

<p>Usage: $ command</p>

<h5>• One-liner commands - CamelCase to kebab-case</h5>
<pre><code>
$ mv "CamelCaseExample.txt" "$(echo "CamelCaseExample.txt" | sed -e 's/\([A-Z]\)/-\L\1/g' | sed -e 's/^-//')" 
$ echo "MyDirectoryFileLine" | sed -e 's/\([A-Z]\)/-\L\1/g' 
$ echo "MyDirectoryFileLine" | sed -e 's/\([A-Z]\)/-\L\1/g' -e 's/^-//' 
$ echo "MyDirectoryFileLine" | sed -e 's/\([A-Z]\)/-\1/g' -e 's/^-//' 
$ echo "MyDirectoryFileLine" | sed -e 's/[A-Z]/-\L&/g' -e 's/^-//' 
$ echo "MyDirectoryFileLine" | sed -e 's/[A-Z]/-\l&/g;s/.//' 
$ echo "SomeACRONYMInCamelCaseString" | sed -e 's/\([a-z]\)\([A-Z]\)/\1-\L\2/' | sed -e 's/\(.*\)/\L\1/') 

</code></pre>

<!-- ########## -->

<h5>Batch processing built-in commands to rename</h5>

<p>Usage: "$ cd /folder" and "$ command"</p>

<pre><code>
• Batch Processing - Rename by replacing
$ for f in *.jpg; do mv "$f" "$(echo "$f" | sed s/IMG/VACATION/)"; done 
• Batch Processing - Spaces to Dashes 
$ for f in *; do mv "$f" "$(echo "$f" | tr ' ' '-')"; done 
• Batch Processing - Uppercase to Lowercase 
$ for f in *; do mv "$f" "$(echo "$f" | tr 'A-Z' 'a-z')"; done 
• Batch Processing - Lowercase to Uppercase 
$ for f in *; do mv "$f" "$(echo "$f" | tr 'a-z' 'A-Z')"; done 
• Batch Processing - CamelCase to snake_case 
$ for f in *; do mv "$f" "$(echo "$f" | sed -E 's/([A-Z])/_\1/g' | tr 'A-Z' 'a-z')"; done 
• Batch Processing - snake_case to CamelCase 
$ for f in *; do mv "$f" "$(echo "$f" | sed -r 's/(^|_)([a-z])/\U\2/g')"; done 
• Batch Processing - Title Case (First letter of each word capitalized) 
$ for f in *; do mv "$f" "$(echo "$f" | sed -E 's/(^|_)([a-z])/\U\2/g' | sed -E 's/_/ /g')"; done 
• Batch Processing - Title Case with Spaces to snake_case 
$ for f in *; do mv "$f" "$(echo "$f" | tr ' ' '_' | tr 'A-Z' 'a-z')"; done
</code></pre>

<!-- ########## -->

<h5>Others</h5>

<p>Convert Camel case to kebab-case</p>

<pre><code>
• Simple command 
$ echo "MyDirectoryFileLine" | sed -e 's/\([A-Z]\)/-\L\1/g' -e 's/^-//' 
</code></pre>

• Batch command

<pre><code>
$ find . -maxdepth 1 -type f -name '*[A-Z]*' -exec bash -c 'mv "$0" "$(echo "$0" | sed -e "s/\([A-Z]\)/-\L\1/g" -e "s/^-//")"' {} \;
</code></pre>

<p>Kebab-case to CamelCase</p>

• One-liner command

<pre><code>
$ echo "my-directory-file-line" | sed -r 's/-(.)/\U\1/g' 
</code></pre>

• Batch command

<pre><code>
$ find . -maxdepth 1 -type f -name '*-*' -exec bash -c 'mv "$0" "$(echo "$0" | sed -r "s/-(.)/\U\1/g")"' {} \;
</code></pre>

<p>Kebab-case to snake_case</p>

<p>• One-liner command</p>

<pre><code>
$ echo "my-directory-file-line" | sed 's/-/_/g' 
</code></pre>

<p>• Batch processing command</p>

<pre><code>
$ find . -maxdepth 1 -type f -name '*-*' -exec bash -c 'mv "$0" "$(echo "$0" | sed "s/-/_/g")"' {} \;
</code></pre>

<p>PascalCase to snake_case</p>

<p>• One-liner command</p>

<pre><code>
$ echo "MyDirectoryFileLine" | sed -r 's/([A-Z])/_\L\1/g' | sed 's/^_//' 
</code></pre>

<p>• Batch processing command</p>

<pre><code>
$ find . -maxdepth 1 -type f -name '*[A-Z]*' -exec bash -c 'mv "$0" "$(echo "$0" | sed -r "s/([A-Z])/_\L\1/g" | sed "s/^_//")"' {} \;
</code></pre>

<!-- ########## -->

<h4>Renamers in shell functions</h4>

<p>
To incorporate the script into your .bashrc or .bash_profile configuration file,
follow these steps:
</p>

<p>
Open your .bashrc or .bash_profile file using a text editor. For example, you
can use nano:
</p>

<pre><code><span>$ </span>ano ~/.bashrc</code></pre>
<button onclick="navigator.clipboard.writeText('nano ~/.bashrc')">Copy</button>
<p>
Add the script function camel_to_kebab() along with the necessary helper
function is_encrypted() to the file. You can copy the entire camel_to_kebab()
function along.
</p>

<p>
Save and exit the text editor. In Nano, you can do this by pressing Ctrl + O to
write the changes and Ctrl + X to exit.
</p>

<p>Source your updated configuration file to apply the changes immediately:</p>

<pre><code><span>$ </span>source ~/.bashrc</code></pre>
<button onclick="navigator.clipboard.writeText('source ~/.bashrc')">Copy</button>
<p>or</p>

<pre><code><span>$ </span>source ~/.bash_profile</code></pre>
<button onclick="navigator.clipboard.writeText('source ~/.bash_profile')">Copy</button>
<p>
You can use it in any directory to convert CamelCase filenames to Title Case.
For example:
</p>

<pre><code><span>$ </span>camel_to_kebab /file/dir</code></pre>
<button onclick="navigator.clipboard.writeText('camel_to_kebab /file/dir')">Copy</button>
<!-- ##### -->

<h5>Camel to kebab</h5>

<pre><code>
camel_to_kebab() { for f in *; do new_name="$(echo "$f" | sed -e 's/\([A-Z]\)/-\L\1/g' | sed -e 's/^-//')" if [ "$f" != "$new_name" ]; then mv "$f" "$new_name" fi done }
</code></pre>

<!-- ##### -->

<h5>Kebab to title case</h5>
<pre><code>
find . -maxdepth 1 -type f -name '*-*' -exec bash -c ' kebab_to_title() { echo "$1" | sed -E "s/-/_/g" | awk '\''{ for (i = 1; i &lt;= NF; i++) { if (tolower($i) ~ /^(in|on|at|of|and|or|but|to|the|a|an)$/) { $i = tolower($i) } else { $i = toupper(substr($i, 1, 1)) tolower(substr($i, 2)) } } print $0 }'\'' FS="_" OFS="_" } for file in "$@"; do base="${file%.*}" ext="${file##*.}" ew_name=$(kebab_to_title "$base") if [ "$base" != "$new_name" ]; then mv -v "$file" "${new_name}.${ext}" fi done ' _ {} +
</code></pre>

<!-- ##### -->

<h5>Camel to title case</h5>

<pre><code>
 camel_to_title() { convert_to_title() { echo "$1" | sed -E 's/([a-z])([A-Z])/\1 2/g' | awk '{ for (i = 1; i &lt;= NF; i++) { if (tolower($i) ~ /^(in|on|at|of|and|or|but|to|the|a|an)$/ && i != 1) { $i = tolower($i) } else { $i = toupper(substr($i, 1, 1)) tolower(substr($i, 2)) } } print $0 }' OFS=" " } for file in *; do if [[ -f "$file" ]]; then base="${file%.*}" ext="${file##*.}" new_name=$(convert_to_title "$base") if [ "$base" != "$new_name" ]; then mv -v "$file" "$new_name.${ext}" fi fi done }
</code></pre>

<!-- ##### -->

<h5>Rename</h5>
<pre><code><span>$ </span>sudo apt install rename</code></pre>

<pre><code>
• Commands for rename 
• Syntax 
$ rename [options] 's/[pattern]/[replacement]/' [file name] 
• Replacing the blank space with an underscore (_) 
$ rename -v 'y/ /\_/' *.pdf 
$ rename -v 'y/ /\_/' ~/Downloads/* 
$ rename -v 'y/ /\_/' ~/Downloads/*.pdf 
$ rename -v 'y/\n/\_/' ~/Downloads/*.pdf 
$ rename -v 'y/\-/\_/' ~/Downloads/*.pdf 
• Commands to rename to numbered order 
$ cd /Files 
• Test the output before (* -n) 
$ rename -n 's/.+/our $i; sprintf("input%03d.png", 1+$i++)/e' * 
• Apply the change 
$ rename 's/.+/our $i; sprintf("input%03d.png", 1+$i++)/e' * 
• Delete a Part of a Filename 
$ rename -v 's/example//' *.pdf 
• Convert Uppercase to Lowercase Characters #FAIL 
$ rename -v 'y/[A-Z]/[a-z]/' *.PDF 
$ find my_dir -type f -execdir rename 'y/A-Z/a-z/' {} \; 
• Convert Lowercase to Uppercase Characters #FAIL 
$ rename -v 'y/[a-z]/[A-Z]/' *.pdf 
• Convert to Camel case 
$ rename 's/ /_/g' *
</code></pre>

<!-- ########## -->

<h4>Metadata Renamer</h4>
• Rename files into directories according to metadata contained in.<br>
• Exiftool Pseudo Tags - https://exiftool.org/filename.html<br>
• Illegal characters in Windows file names.<br>

<h5>• Basic of metadata</h5>

<pre><code><span>$ </span>exiftool -a input.pdf</code></pre>

<pre><code><span>$ </span>exiftool -a -s input.pdf</code></pre>

<pre><code><span>$ </span>exiftool -a -G1 input.pdf</code></pre>

<pre><code><span>$ </span>exiftool -G1 -s 'input.pdf' | grep '\[PDF\]'</code></pre>

<pre><code><span>$ </span>pdfinfo input.pdf</code></pre>

<pre><code><span>$ </span>pdfinfo -meta input.pdf</code></pre>

<p><small>
-a shows all metadata tags across all groups (EXIF, IPTC, XMP, etc.).<br>
-s shows metadata tags in a short format, without grouping by metadata type.<br>
-a -G1 shows all tags, including those not normally extracted, and groups them
by family 1 (e.g., PDF tags grouped under [PDF]).
</small></p>

<h6>• Rename by creation date and time tags [20060327_1058-2.jpg]</h6>
<pre><code><span>$ </span>exiftool -d %Y%m%d_%H%M%%-c.%%e "-filename&lt;CreateDate" /file.jpg</code></pre>
<h6>• Rename by title tag [title.pdf]</h6>
<pre><code><span>$ </span>exiftool '-filename&lt;Title ' /input.pdf</code></pre>
<h6>• Rename by title and author tags [Title - Author .pdf]</h6>
<pre><code><span>$ </span>exiftool '-filename&lt;$Title ${Author}.%e ' /input.pdf</code></pre>
<h6>• Rename by title, author and date tags [Title - Author (Year).pdf]</h6>
<pre><code><span>$ </span>exiftool '-filename&lt;$Title - ${Author} (${Date#;DateFmt( "%Y")}).%e ' /input.pdf</code></pre>

<pre><code><span>$ </span>exiftool '-filename&lt;$Title - ${Author} (${CreationDate#;DateFmt( "%Y")}).%e ' /input.pdf</code></pre>
<h6>• Recursively</h6>
<pre><code><span>$ </span>exiftool -r '-filename&lt;${Title} - ${Author}.%e ' /DIR -ext pdf</code></pre>

<pre><code><span>$ </span>exiftool -r '-filename&lt;${Title} - ${Author} (${CreationDate#;DateFmt( "%Y")}).%e ' /DIR -ext pdf</code></pre>
<h6>• Rename by title, author and date tags [Title - Author (Year).pdf] and insert snake case format
</h6>
<pre><code><span>$ </span>exiftool -r '-filename&lt;${Title;s/ /_/g}_-_${Author;s/ /_/g}_(${CreationDate#;DateFmt( "%Y")}).%e ' /DIR -ext pdf</code></pre>
<br>

<br>
</details>
</div>
