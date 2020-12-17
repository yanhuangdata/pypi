# PEP 503 compliant PyPi repository
## repo url
[https://yanhuangdata.github.io/pypi/simple/](https://yanhuangdata.github.io/pypi/simple/)

## Usage
### poetry
https://python-poetry.org/docs/repositories/#install-dependencies-from-a-private-repository

```
[[tool.poetry.source]]
name = "yh-repo" 
url = "https://yanhuangdata.github.io/pypi/simple/"  
```

### pip install

```shell
pip install pyarrow --extra-index-url https://yanhuangdata.github.io/pypi/simple/
```

## Add new package

1. Create link in the main `index.html` file;
1. Create file `{PACKAGE}/index.html` if it doesn't exist yet;
1. In the file {PACKAGE}/index.html add the following line: `<a href="{URL}#sha256={SHA}>{FILENAME}</a>`, where
    * `{URL}` is a publicly available url of the binary file (which could be hosted on S3 for example);
    * `{SHA}` is obtained from python script 

        ```python -c "import hashlib; print(hashlib.sha256(open('./path/to/your/package.whl', 'rb').read()).hexdigest())"```
    * and {FILENAME} is the name of the wheel file.

## References
* https://www.freecodecamp.org/news/how-to-use-github-as-a-pypi-server-1c3b0d07db2/
* https://github.com/ceddlyburge/python-package-server
* https://github.com/h2oai/py-repo