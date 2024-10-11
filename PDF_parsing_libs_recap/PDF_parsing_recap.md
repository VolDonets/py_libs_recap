# Tested libraries, tools and services

> 0. Default lib __UnstructuredPDFLoader__, provided by __LangChain__
> 1. lib __PyPDF2__
> 2. lib __pdfplubmer__
> 3. lib __PDFMiner.six__
> 4. lib __PyMuPDF__ + __PyMuPDF(LLM)__
> 5. lib __Camelot-py__ and __tabula-py__
> 6. tool __Marker__
> 7. service __LlamaParse__

# Short review on PDFs used in testing
## 1. simple-text.pdf

> Pages: 2.

> Contains a few paragraphs of text with topic names.

## 2. table.pdf

> Pages: 2

> One, simple well-formatted table on 2 pages. The last lin e of table is on the last page.

## 3. table-text.pdf

> Pages: 1

> Contains simple table and a few lines of text.

## 4. complex_text.pdf

> Pages: 60

> Contains many lines of text. With lists and a few possible tables (not exactly).

## 5. complex_text-tables-images.pdf

> Pages: 186

> Contains images, text, text in columns, simple tables, complex tables and large tables.

## 6. complex_columns-text-tables.pdf

> Pages: 6

> Contains text in 2 columns, images, simple tables, and math equations.

## 7. GeoBase_NHNC1_Data_Model_UML_EN.pdf

> Pages: 19

> Contains text, contains tables and text in diagram formats.
 
# Short review on each tested lib, tool and service
## 0. Default lib __UnstructuredPDFLoader__, provided by __LangChain__

> Pros:
> - fast
> - works with text only PDFs files

> Cons:
> - do NOT support table extraction
> - makes text in table unordered
> - do NOT support text in columns

## 1. lib __PyPDF2__

> Pros:
> - allows image extraction
> - fast
> - extract fine text from tables

> Cons:
> - do NOT provide adequate table markdown, so you cannot discriminate table from plain text
> - some PDFs with text has strange extraction with discrimination words by '\n' instead of ' '
> - hard to read formulas

> Strange:
> do NOT extruct whole PDF in one text object, just do it by pages

## 2. lib __pdfplubmer__

> Pros:
> - fine table extraction in array of arrays
> - fine text extraction in single-column PDFs

> Cons:
> - struggling with 2 & more column text extraction
> - NOT fine documentation

> Strange:
> - extracting block-schemas as strange tables // pretty confusing

## 3. lib __PDFMiner.six__

> Pros:
> - native API for parsing PDFs

> Cons:
> - you need to hardcode everything here from text extraction to everything like tables

## 4. lib __PyMuPDF__ + __PyMuPDF(LLM)__

> Pros:
> - very similar to **pdfplumber** in parsing tables task
> - fixes problem of two columns text
> - provides integration with LLM & RAG, also has integration with **LangChain**
> - can parse PDFs into Markdown format

> Cons:
> - strange parsing for some tables

## 5. lib __Camelot-py__ and __tabula-py__

> Pros:
> - return tables in __Pandas__ format
> - in clear tables give correct table representations, which might require small fixing
> - recognize and process right even big tables

> Cons:
> - sometimes do NOT recognize a table in the right way and leave empty table
> - struggling with tables without line delimiters, although process them better than __PyMuPDF__
> - do not recognize other parts of PDFs like plain text

## 6. tool __Marker__

> Pros:
> - Parse even untexteorized PDFs (like photo PDFs or scans) using OCR model
> - Work well with all kind of PDFs and their structures
> - Provide Markdown of PDFs which include text formating, table formating, image blocks (might be useful in the future iteration of the project)

> Cons:
> - Requires GPU otherwise it will take enormous time amount for parsing PDFs, especially big ones
> - Sometimes uncorrectly parse tables, especially with strange formatting

> Strange:
> - do NOT provide Python API for direct use in Python program, but provide console util or allow running this as independent service

## 7. service __LlamaParse__

> Pros:
> - Simple API
> - Free scanning of 1000 pages per day, and the next page will cost 0.003 per page
> - Works similar to __Marker__ tool, but significantly faster
> - Use LLMs for postprocessing, sometimes extract information hidden in text

> Cons:
> - Have similar issues with quality of parsing.
> - Have issues with text ordering, especially in multicolumn PDFs.
> - Have issues with parsing tables on a few pages.