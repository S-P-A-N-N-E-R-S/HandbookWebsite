# HandbookWebsite

First, make sure you have a current version of Python and pip installed:

```
$ python --version
Python 3.8.2
$ pip --version
pip 20.0.2 from /usr/local/lib/python3.8/site-packages/pip (python 3.8)
```

Then, install mkdocs
`pip install mkdocs`

Run
```
$ mkdocs --version
mkdocs, version 1.2.0 from /usr/local/lib/python3.8/site-packages/mkdocs (Python 3.8)
```
to check whether everything worked fine.
Check out the ![installation guide](https://www.mkdocs.org/user-guide/installation/) when you detected errors.

Now that you can run mkdocs, clone the repo  
using SSH `git@gitpgtcs.informatik.uni-osnabrueck.de:spanners/handbookwebsite.git`  
or HTTPS `https://gitpgtcs.informatik.uni-osnabrueck.de/spanners/handbookwebsite.git`

and run `mkdocs serve` to view a local version of the website, which will be automatically updated when you save your files (listening on `127.0.0.1:8000/`).

You can only update the files and your local version of the website, only @blechtermann has been granted the permission to work on the real website, available at https://project2.informatik.uni-osnabrueck.de/spanners/.