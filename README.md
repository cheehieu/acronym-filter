# Overview

This acronym-filter script was written to automate the process of generating a glossary of acronyms used during the Axiom Module system requirements review (SRR) on September 1, 2016. It scans a Word .DOCX document and puts every unique acronym (a consecutive sequence of capital letters, symbols, or numbers) into a dictionary. If applicable, the acronyms are matched to an imported .CSV dictionary file to retrieve the acronym expansions. The newly found list of acronyms is saved to an output_dict.csv dictionary file, where it can be manually modified with Excel. An output_glossary.docx file is also generated from the input dictionary, which can then be used for final publishing of an acronym glossary. 

Note: you may need to install lxml and python-docx dependencies.
```
$ pip install lxml
$ pip install python-docx
```

# Usage
## General Usage:
```
$ python acronym-filter INPUT_FILE.docx INPUT_DICT.csv
```
Note: INPUT_DICT.csv is optional.

## Test Example:
```
$ python acronym-filter Prelim_Axiom_Reqmnts.docx axiom_glossary.csv
```
The script should create two output files: "output_dict.csv" and "output_glossary.docx". The output dictionary is a new dictionary (appended from the imported dictionary, if applicable) that contains empty fields for the expanded forms of undefined acronyms. The output glossary is a MS Word document of the fully defined acronyms found.

# Limitations
* Acronyms must begin with a capital letter and end with another captial letter or number. Thus, lowercase abbreviations such as units (mm, dBA, etc.) will not be captured by the script. But ACRONYM_REGX can be modified to change this search pattern.
* Long acronyms are not captured. A workaround was used because the IRD requirements were written using all caps. Change MAX_ACRO_LENGTH to tune.
* Identical acronyms (with different expansions) are not captured. The script filters duplicate acronyms without using any contextual differentiation.

# Useful Resources
* http://spaceflight.nasa.gov/cgi-bin/acronyms.cgi
* http://www.nasa.gov/directorates/heo/scan/definitions/acronyms/index.html
