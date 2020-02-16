# tableToDocument

Python library for easily writing python data to human readeble documents.Current supported
python data types are  `str, int,list,dictionary,set,pandas series` and `pandas Dataframe`.
Current supported file formats for writing are `.doc,.docx,.odt` and `.tex`.

## Installation

### Pypi

You can easily install and use the library with PyPi 
```
pip install tableToDocument
```

### Git
Clone this repo to your local filesystem
```
git clone https://github.com/pgiank28/tableToDocument.git
```
To run from source you must change all the `import tableToDocument.x` to `import x` from all the files.
After that,see the tests files at /tests directory for how to make your own files that can write data to documents

## Usage
If you've downloaded the library by PyPi, then a python version >= 3.5 and the pandas framework running at your machine 
are the minimum requirements.You can run in your python console
```
import tableToDocuments.toDoc as td
```
to use the library.The toDoc module is the only you will propably use.You can then write to a word document by calling the
toWord method and to a latex document by calling the toTex method
```
td.toWord(path_to_file,flag,data)
td.toTex(path_to_file,flag,data)
```
where `path_to_file` is the location of the file you wish to write the data to, and data is the data you are about to write.
The flag property takes the following values <br/>
`"a"` for appending to the end of the file.For tex files, appends to the bottom of the last \\{section}.<br />
`"b"` for writing at the beginning of the file.For tex files,writes at the top of the first \\{section}.<br />
`#some_integer_num` for writing at the specific line num of the document.For tex files,writes at the bottom of the 
section num.

If you've downloaded the source code from the git version , simply go to the location you have saved your own test files
(see above) and execute `python myfile.py`

## Example
`td.toWord('/some/path/file.odt',14,{'a':[12,14,16'],'b':3,'f':[11,19,20,78,90]})` writes at the line 14 of the document the following
table
|a  |[12,14,16]|
|---|------|
|b  |3|
|f  |[11,19,20,78,90]|

`td.toWord('/some/path/file.odt','a',pandas.Dataframe({'a':[12,14,16'],'b':[3,88,90],'f':[11,19,20]})` writes at the end of the document
the following table
|  | a |b  |f |
|--|---|---|--|
|0 |12 |3  | 11|
|1| 14 |88 |19|
|2| 16 |90 |20|

In latex documents,the arrays are written like above,but without borders, after you convert the document to pdf.
## Links
You can see the pypi location
