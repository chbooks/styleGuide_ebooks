#The Coach House Manual of Style: An Opinionated Guide to Making Ebooks

##Before You Start

* This guide is licensed under [CC BY-SA 2.5 CA](http://creativecommons.org/licenses/by-sa/2.5/ca/) which means (among other things) if you  build upon the material, you must distribute your contributions under the same license as the original.
* This guide is a work in progress. We aren't eproduction experts by any means, so if you take issue with anything below (Are we wrong? Misguided? Too wordy?), then please initiate a pull request (yeah Github!). You will be our friend forever.
* This guide primarily regards ePub 2.0.1 and Kindle. Updates or additional docs for epub3 will be added later.
* We don't create books in fixed layout, or with sync, or with audio and video, or with gesture support. When the time comes we will add guidelines for those features.
* We use [KindleGen](https://kdp.amazon.com/help?topicId=A3IWA2TQYMZ5J6) to create and test ebooks for Amazon. We make our files for Amazon _after_ we make the epub ready for sale. In other words we use KindleGen to convert our epubs to Kindle files as late in the eproduction process as possible. What follows are generic guidelines for all vendors including Amazon. If there is an issue specific to the Kindlegen conversion, that will be noted alongside the instructions for the epub.

Cool? Ok. Let's get started.

---
##Purpose of This Guide

So what the heck is this and how should it be used?

####Who
This guide is for ebook developers using whatever toolchain they prefer. (The formatting guidelines for authors are elsewhere.)

####What
The idea behind this guide is to standardize the ebook output from Coach House Books; eproduction the Coach House way™. It's not about process. It's about output. We assume you have a process that works for you. So this more of a reference quide than a step-by-step how-to. Basically we want to be able to point to this guide — and with little further explanation — say "like this".

---
###Us Being Pedants

Before we get too far, we might as well get some pedantic stuff out of the way... yes we care how the text is encoded. We care about semantic tags. We care about French spacing and emdashes. We care a lot. We want our ebooks to be as near to bulletproof as possible.

That means before a work is typeset we typically strip it down to its raw form and build it back up from there.

When preparing text for inclusion in an ebook, that means four things:

1. First, no ASCII. No ANSI. No Latin-1. No Mac roman. And hell no Windows-1252 or similar. Unicode all the way; UTF-8 to be specific. If you don't know what we are talking about, please go read [Joel Spolsky on the topic](http://www.joelonsoftware.com/articles/Unicode.html) (we'll wait).
2. Second, we prefer the text be transcoded to UTF-8 rather than simply declared as UTF-8 in the header. If it says it's UTF-8 on the tin, please ensure that's what it is. In practice that means you'll probably have to change the encoding preferences in your text editor. If you are tempted to blindly copy & paste from MsWord into an HTML doc while declaring UTF-8 at the top, please think twice. It's quick and dirty and it works. We get it. But in our experience, this causes problems elsewhere, so please avoid doing this if you can.
2. Third, we like proper punctuation. We like typographer's quotes. We like emdashes. And we like one space between sentences. In our device testing we've found &mdash; provided you do items one and two above &mdash; the need to use HTML entities for every type of punctuation can be minimized. Our advice: use HTML entities to get the job done, but if the unicode punctuation looks fine during QA, don't feel you need to add in HTML entities for their own sake.
3. Fourth, we like semantic mark-up. We like lists to be in list tags. We think [there is a difference between text that is italicized and text that is emphasized](http://learn.shayhowe.com/advanced-html-css/semantics-accessibility/). We think abbreviations and addresses and alt-text should be coded properly. Having said that we understand this can be overkill. We won't be paying you enough to definitively weigh in on whether LASER should be coded as an acronymn or not. Just please take care and please be consistent.

---
###Our House Style: Punctuation

Typically text will have been edited _before_ it is sent for assembly but in certain cases it is handy that the ebook developer know a little about our practices upstream of the creation of the ebook. Here is a selection of entries from our house style that may be relevant during production.

__Commas:__ The Oxford comma, yes please.

__Dashes:__ Our house-style dictates spaces on either side of dashes. If they aren't present, please add them in.

__French Spacing:__ No thank you.

 
---

## File and Folder Conventions
###Why We Think Conventions Are Important
At Coach House we like speed and efficiency. If you can create an ebook for us in record time, then that's great. But speed and efficiency at the outset isn't everything that matters. When creating ebooks for us we would like you to think of the entire lifespan of the file.

We hate rework.

If we open up your file two years from now and it takes us 20 minutes to figure out how it was put together, then you aren't doing us any favours.

To that end, we have outlined our preferred conventions below. These are our preferences but needn't be taken as the law.

The idea here is if the conventions are followed, then there will be consistency across our catalog. No matter the age of the title, we should be able to drop in the template for our copyright page and have it validate with the minimum of changes. If all of our files are constructed differently then that's not going to happen.

Did we mention we hate rework?

So we understand having all files in a single folder is less effort. And we understand that using abbreviations in filenames is less typing. And we understand that exporting epubs from programs like InDesign can be fast and easy. And we understand that, in such a scenario, modifying the InDesign-created file names to mirror our preferences would be counterproductive. We get it. But we are also big fans of human-readable file names and logical file structure. (We'll say it again: we hate rework.) These are our preferences. We won't hold you to them. Just know they are carefully considered. So if you are using shortcuts, macros, scripts, or programs to process a file for us, go as quickly as you like but please take as much of the the below into consideration as makes sense.

Thanks in advance.
 
###Formatting

* We prefer spaced-indentation over tabbed-indentation. Two spaces per logical level is perfect. We also, [taking more pointers from the Ruby community](http://www.caliban.org/ruby/rubyguide.shtml#indentation), encourage you not to use tabs ever.
* We prefer Unix line breaks (LF) just because they are easier to search and replace. If your editor has a preference setting for that, please use it.
* We prefer omitting white spaces after closing tags or at the end of lines. Since we use GIT, and GIT recognizes whitespaces as trackable characters, we prefer if you leave them out. Again, if your editor has a preference setting for this, please turn it on and delete unnecessary spaces.

###Folder Naming

The standard epub2 files and folders are required at the top level. 

* mimetype
* META-INF
	* container.xml
* OEBPS
	* .ncx
	* .opf 		 	

We prefer putting the .ncx and .opf files in the OEBPS folder.


We prefer the .ncx file to be named 'navigation.ncx' to avoid confusion with the contents or the toc file.

We prefer the .opf file to be named 'manifest.opf'. Alternately, metadata_manifest_spine.opf or a similar name that describes what it is/does.

We also prefer the OEBPS folder name, instead of OPS. OEBPS stands for Open eBook Publication Structure. We are simply old-school on this point.

As a rule, all names for folders created by the developer are plural &mdash; 'styles', 'assets', 'contents', etc. We don't mind if you use css or js for the names of the Styles or the Scripts folders respectively. But generally we like the idea of keeping all folder names plural so we will never have to cross-reference the name for a file path again.

###Folder Organization

We are big fans of discrete folders for different types of files. We follow the web designers' convention of placing scripts, styles, and content in separate folders. We also like keeping image-type content and text content separate.

So the hierachy in our typical OEBPS folder might look like the following:

* oebps
	* assets
	* contents
	* css
	* js
	* manifest.opf
	* navigation.ncx

The contents folder should only contain xhtml files. Fonts, photos & illustrations, and icons & logos can go in the Assets folder. As a rule: if &mdash; theoretically &mdash; a file could be used in multiple locations throughout a book, then it belongs in the Assets folder. If a file is used once in book, e.g, chapter01.xhtml, then it belongs in the Contents folder.

###File Naming

* As per the epub specification, filenames have to start with a letter or number.
* We prefer filenames be word-separated in all lower case
* We prefer underscores in file names instead of dashes.
* We prefer using the .xhtml file extension, instead of .html, so that the file extension is consistent with the doc type declaration within the file. The html extension should be reserved for epub3 files.
* We prefer non-abbreviated, semantic file names. chapter01.xhtml instead of ex-ch01.xhtml
* We prefer generic file names instead of project-specific ones. cover.png instead of 9780061835384.png
* We prefer file names to be the same length when possible. chapter01.xhtml and chapter11.xhtml instead of chapter1.xhtml and chapter11.xhtml
* In all the examples and templates in this guide, files are named so that they sort in a natural order on your computer (frontmatter files have prefixes in the 0-99 series, backmatter files start at 200, etc.). In a real-world production scenario, we would not be picky about this.

In general, if a file appears consistently across all the titles in our catalog (e.g. about_the_publisher.xhtml or stylesheet.css) we would like it to be consistently named and located across all the titles in our catalog.

-----

##What We Talk About When We Talk About Ebooks

###Parts of a Typical ePub [^1]
#####Mimetype

* It reads `application/epub+zip`. No returns or line breaks should be included.
* Not much else to say about this file other than when zipping the book folder into the epub, keep this one at the top.

#####META-INF

######encryption.xml 
* The epub specification states that the encryption.xml file should go in this folder. Since we don't DRM our books or our fonts, we don't really care about this. And if we did DRM our books, the DRM is applied by the retailer anyway, so it still would be left out.

######container.xml
* The conventional format for this file works for us as is. Remember to modify the full path of the rootfile as needed:
`<rootfile full-path="OEBPS/manifest.opf" media-type="application/oebps-package+xml"/>`

#####OEBPS/navigation.ncx

* __Naming__: The industry convention is to name this file 'toc.ncx'. We prefer the more descriptive 'navigational_toc.ncx' or the shorter but still meaningful 'navigation.ncx'
* __Metatags__: The unique id or uid is always the 13 digit ISBN of the edition, without hyphens.
	* `<meta name="dtb:uid" content="9780000000000"/>` 
* __Metatags__: The respective depth of the navigation should be reflected using the depth meta-element. For the majority of our books this value is 1, but that's not to say we don't have more layered titles in our catalog, so this value is always worth double checking after the navmap is completed.
	* `<meta name="dtb:depth" content="1"/>`
* __Metatags__: The total page count and max page count meta-elements should be included but their values can be left at zero.
	* `<meta name="dtb:totalPageCount" content="0"/>`
	* `<meta name="dtb:maxPageNumber" content="0"/>`
* __Metatags__: Details on the meta-element for the cover image TK
	* `<meta name="cover" content="02_assets/101_cover.jpg" />`
* __Metatags__: Details on the page list meta-element TK
* The doc tite tag should be included irrespective of whether this data is viewable on your test device.

#####OEBPS/manifest.opf

* Make sure the manifest.opf file path is referenced properly by the container.xml file in the META-INF directory.
* Include the unique id here as well. This is the same id as in the header of the navigation.ncx file. It is always the 13 digit ISBN of the edition, without hyphens and it will be repeated as the identifier (for Dublin Core) in the metadata section below.  

There are __four__ sections in this file: metadata, manifest, spine and guide.

######1. Metadata

* Reference both the Dublin Core and Open Packaging Format specifications in the metadata.
* Use both the /terms/ namespace and the /elements/1.1/ namespace for Dublin Core.
* Make sure to declare all three as namespaces in the header of the metadata section
	* `<metadata 
	 xmlns:dc="http://purl.org/dc/elements/1.1/"
	 xmlns:dc="http://purl.org/dc/terms/"
     xmlns:opf="http://www.idpf.org/2007/opf">`
* Include the following tags
	* dc:title
	* dc:identifier and opf:scheme="ISBN"
	* dc:date and opf:event="original-publication"
	* dc:language (en)
	* dc:publisher (Coach House Books)
	* dc:creator opf:role="aut" opf:file-as="LastName, First" [^2]
	* dc:subject (since this field can appear in the navigation of some ereading systems, use the [BISAC subject heading](https://www.bisg.org/complete-bisac-subject-headings-2013-edition), not the code itself)
* As a meta property, include the date last modified
	* `<meta property="dcterms:modified">2012-05-04</meta>`
* As a meta name, include the cover ID
	* `<meta name="cover" content="my-cover-image" />`
* Do not include pricing or rights details in the metadata header	
		
	 	  	
######2. Manifest

* Include the id name, the href, and media-type of each file in the ebook.
* We prefer the file name be related to the id name in an obvious way
	* e.g. item id="cover_image" href="cover_image.jpeg" 
	OR item id="cover_page" href="cover_page.xhtml"
* List the files in as near to spine order as you can. Include the css files at the top and the assets (images, fonts, etc.) at the bottom.
* To make the manifest easy to read, we prefer the media-type be listed first, the id second, and the href last.
	* `<media-type="application/xhtml+xml" item id="chapter05" href="chapter05.xhtml" />` 	
	 
######3. Spine Order

*  Use the linear="no" designation for any auxilary content or '[XML islands](http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm#Section2.4.3)' in the book.
*  By default, list the cover page: linear="no"

Here is the preferred spine order in sequence. (Not all parts will appear in every book.)

######Spine Order: Front Matter

| File			|	Guide Reference	Type		         |
|----------------|-------------------------------------|
|0. Cover page	|	reference type="cover", linear="no"
|1. Title		|	reference type="title-page"
|2. Dedication	|	reference type="dedication"
|3. Epigraph	|	reference type="epigraph"
|4. Contents	|	reference type="toc"
|5. Foreword	|	reference type="foreword"
|6. Preface		|	reference type="preface"
|7. Introduction|	reference type="text"

######Spine Order: Back Matter

| File			               |	Guide Reference Type              |
|------------------------------|-------------------------------------|
|09. Footnotes/Endnotes			| reference type="text"
|10. Acknowledgements			| reference type="acknowledgements"
|11. Appendix					| reference type="text"
|12. Notes						| reference type="notes"
|13. Glossary					| reference type="glossary"
|14. Bibliography or References| reference type="bibliography"
|16. Colophon (if required)		| reference type="colophon"
|17. Copyright					| reference type="copyright-page" 
|18. About the Author(s)		| reference type="text"
|19. About the Publisher		| reference type="text"

######4. Guide

* Although the Guide is a vestige of older reading systems, it is still required by a number of our vendors, so if it is not present please add it in.
* Guide items are an optional feature in the EPUB format. Kindle provides support for the cover, TOC, and text guide items.
* Take specific care to note the first file with [a type](http://www.idpf.org/epub/20/spec/OPF_2.0.1_draft.htm#Section2.6) other than 'cover' or 'title-page' as that file is typically shown to readers first when they open a book after purchase. Our preference is either the foreword, preface, or first chapter be the first file to be revealed to the reader. This varies reading system to system.
* By convention (see above) we prefer underscores for spaces. Take note that reference types use hyphens. i.e. copyright-page
* Also by convention we prefer descriptive file names to differentiate the cover image from the cover page. Contrary to this, the reference type for the guide must be simply 'cover'.
* And remember, reference types are case sensitive.
* HTML TOC Must Be Referenced as a Guide Item
* The Kindle platform supports guide items for defining the cover, the table of contents (TOC), and the start reading location (”Go to Beginning”).
* Amazon does not recommend adding additional guide items to the OPF file, because they will be grayed out in the menu options and may cause customer confusion.

###Content Divisions

See below for more detail on the typical parts of a published work:

| Part							| Spine Order	 | Notes|
|------------------------------|:-------------:|------|
| Cover page					| 00 			| 
| Book Half Title				|    			| Remove.
| Series Title					| 				| Remove. Add to title page
| Title							| 01			| 
| Copyright						| 16			| If in frontmatter, move to backmatter.
| Dedication					| 02			|
| Epigraph						| 03			|
| Contents						| 04			| If not in print version, should be added.
| Foreword						| 05			| 
| Preface						| 06			|
| Acknowledgements				| 08 			| If in frontmatter, move to backmatter. 
| Introduction					| 07	
| Chapters						| 				| Remove half tiles for chapters.
| Appendix						| 09			|
| Notes							| 10			|
| Glossary						| 11			|
| Bibliography or References 	| 12			|
| About the Author(s) 			| 17			|
| Illustration/Photo Credits	| 13			| Remove. Move to copyright page.
| Indexes						|				| Remove.
| Colophon						| 15			| Consult with managing editor.
| About the Publisher 			| 18			|


####Cover Page
* Not to be confused with the cover image. The cover image (jpeg) is included on the cover page (xhtml).[^3]
* The cover page is mandatory for every book. If the cover image from the print edition is not cleared for digital distribution, a generic place holder image should be included in its place on the ebook's cover 'page'.
* Notes aboout Kobo and SVG TK
* The background color on HTML in-book cover pages should be undefined. Specifying colors results in uneven, dark borders around the cover image on the cover page.

####Titles
* Our general philosophy is if the print edition has several types of title pages, this information should be condensed to a single file in the ebook. i.e, book half titles should be deleted and series title information should be incorporated with the main title.

####Copyright
* If in the frontmatter, move to the backmatter
* Generally the file for the copyright 'page' in the ebook should be constructed in the spirit of the closing credits of a film &mdash; it's the place the publisher takes care of business. 
* In addition to the standard things from the print edition &mdash; an ISBN, an address, a copyright statement etc. &mdash; this file should also contain the publisher's acknowledgements, image credits, design credits, and any other small print.
* Notes about the library of canada classifications are TK
* Versioning information TK

####Dedication
####Epigraph
####Contents

* The entries in the TOC must be HTML links so that users can click to go to a specific location. 
* if page numbers are present, from the print edition, please remove them
* "ibooks:reader-start-page" attribute TK
	* `￼<nav epub:type="landmarks">  <ol>    <li><a href="coverpg.xhtml" epub:type="cover">Cover</a></li>    <li><a href="titlepg.xhtml" epub:type="titlepage">Title Page</a></li>    <li><a href="chapter.xhtml" epub:type="bodymatter">Start</a></li>    <li><a href="bibliog.xhtml" epub:type="bibliography">Bibliography</a></li></ol> </nav>` 	
* construct this page as near to the epub3 spec as possible

	`<nav epub:type="toc">    	<ol>      		<li><a href="chapter1.xhtml">Chapter 1</a>         		<ol>          			<li><a href="chapter1.xhtml#figure1">Figure 1</a></li>         		</ol>			</li>      		<li><a href="chapter2.xhtml">Chapter 2</a></li>    	</ol>	</nav>`
* Possible contradictory info from Amazon, check their guidleines	

####Foreword

* QA -- does the ereader open to the foreword when it is present?

####Preface

* QA -- does the ereader open to the preface when it is present?	

####Acknowledgements
####Introduction
####Chapters
####Appendix
####Notes
####Glossary
####Bibliography or References
####Illustration/Photo Credits

* If there are less than 10 required credits for illustrations/images, include them on the copyright page.
* If there are more than 10 required credits for illustrations/images, please consider including a separate table of illustrations in it's own file. Such a table can be referenced in the guide section of the .opf, but this is not mandatory in our eyes.
* If a table of illustrations exists in the print edition and that table refers to the page numbers in the print edition, keep the table but remove the page references.

####Indexes

* If an index is present in the print edition, __remove it from the ebook__
* There are special cases where a digital cross-linked index is important in ebooks but these are exceptions. In those cases, the managing editor at Coach House will identify what kinds of anchor tags will be required in the document structure to further support an e-Index.

####Colophon
* If a colophon exists in the print edition, __remove it__ after consulting with the managing editor.
	* Typically, the print designer is not credited in the ebook.
	* Typically, the creator of the ebook is not credited in the ebook.
	* Typically, the cover designer is given credit but that credit should be included on the copyright page when that makes sense.
	* Typically, the font used in the print edition is not mentioned in the ebook.
* We embed fonts in our ebooks on an exception basis. In those cases, the managing editor may elect to modify the content of the colophon from the print edition to reflect how the ebook was constructed.
 
####About the Author(s)

* The author biography and a list of previous works can be included in the same file.
* If there is 'back-of-jacket' copy from the print edition that praises previous works or endorses the writer alone, then this copy should not included in the ebook.
* At this time, we are not including photographs of the author in the ebook.

####About the Publisher
* We use the same language from book-to-book to describe ourselves.
* The most up-to-date version of this boilerplate is available within the about_the_publisher.xhtml sample file.	
###Page Elements

####Drop Caps

* Drop caps are easy to do on ePub3(Apple) and KF8. They are not as easy to do on older devices that use older file formats. For this reason, we tend to stay away from drop caps. If the print edition has them, we are fine with them be left out of the ebook.

####Page Breaks

* Page breaks are supported in ePub3(Apple) and KF8. They are not supported on older devices that use older file formats. For this reason, we create page breaks the old-fashion way -- by creating a new .xhtml file.

####Indenting

* KindleGen automatically indents the first line of every paragraph by default. We apply an override style for both epubs and Kindles to prevent this.

####Line Height

* No less than 1.2em 

####Anchors

* Anchors Must Be Added Before Formatting Tags `<a name=”Chapter1”/><h1>Chapter 1</h1>`



###Managing Assets

####Cover Art (aka Marketing Image)
* the image delivered alongside the book asset. It does not refer to the cover image included on the cover page.
* The book’s cover art must use RGB color mode and should be at least 1400 pixels along the shorter axis.
* Minimum of 300 dpi.
* A high-quality JPEG with .jpg or .jpeg extension or PNG with .png extension. 
* Kindle books must have a marketing cover image provided for use on the website detail page. The preferred format for the cover is a JPEG image of 2500 pixels on the longest side (with a minimum of 1000 pixels on the longest side).

####Interior Images

* Use the sRGB colour space
* always include the alt tags (a textual replacement for the image.)
* dimensions and positioning using CSS
* Size the image container, not the image itself
* Size the image container using viewport units, not percentages.
* 3.2 million pixel limit
* at least 1.5 times the intended viewing size 
* No words in images. Use an HTML overlay instead
* JPEG with .jpg or .jpeg extension (quality unconstrained) or PNG with .png extension.
	* Transparency = PNG
	* No transparency = JPEG 	
* The maximum recommended size is about 10 MB of un-encoded image data per XHTML file.
* Kindle does nor support transparent PNGs
* Images cannot exceed 127 KB in size
* JPEG format with a quality factor of 40 or higher.
* at least 600 x 800 pixels in size
* Use GIF for Line-Art and Text
	* The MAXIMUM image size is 500 x 600 pixels. This ensures that the image is not shrunk on a Kindle device, which could make the text illegible.
	* The MINIMUM size of text is 6 pixels for the height of a lowercase “a.”
* Place the caption below the related image, so that the reader views the image before the caption.
* width and height cannot both be set to a fixed percentage.		

####Audio and Video

* The height and width attributes of embedded audio and video should be defined in CSS.

####CSS

* Defining Page breaks TK

####Fonts

* to ensure font scaling body 1em
* always define sizes in ems
* For embedded fonts you must set the "specified-fonts" option to true.

----

##Preflight

* If you have tested your file in iBooks or are otherwise using a Mac, remember to discard the system generated .plist file

zip -0Xq book.epub mimetype
zip -Xr9Dq book.epub * -x .DS_Store


###Validate Your Pages

* http://validator.w3.org/#validate_by_upload+with_options
* http://www.w3schools.com/xml/xml_validator.asp

###Validate Your Ebook
* http://validator.idpf.org

###Do Basic ePub QA Testing
* Check the file at the very least on two or more devices (not emulators, devices)
* preview your book in night mode. I

####Validate that the ePub Successfully Converts Using Kindlegen

* Kindle previewer www.amazon.com/kindleformat




[^1]: Commonly referred to as a _vanilla_ epub, one with no added bells and whistles

[^2]: This was a requirement for proper alphabetization in iBooks circa 2010. Not sure if this is still a requirement or not. To be checked in future QA.
 
[^3]: 'Page' is clearly not the right term when talking about assembling ebooks, but we use it here anyway to meaningfuly distinguish between two items

---

Todo:
tabs and spaces
reconcile guide advice between kindle and ibooks
