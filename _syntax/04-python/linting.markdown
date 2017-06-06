---
title:  "Python Linting"
categories: python
---

#### Setup Python Linting

We use [flake8](http://flake8.readthedocs.io/en/latest/index.html) for python linting. 
The following instrutions is based on using the Visual Studio Code text editor.

- On your machine `pip3 install flake8`
- In Visual Studio Code install the Python extension (by donjayamanne)  
    - Open Command Palette `⇧⌘P`
    - Typing `ext install`
    - Search for Python
    - Select the extension from the list 
- Disable the default python linter and enable flake8
    - Open Command Palette `⇧⌘P`
    - Search for and open 'Workspace Settings'
    - Add this code snippet to the custom settings file (normally on the right)

    ```
    {
        "python.linting.flake8Enabled": true,
        "python.linting.pylintEnabled": false
    }
    ```
- The Final step is to add the `.flake8` config file to your project. An example of how this may look: 
```
[flake8]
ignore = 
    # E302: expected 2 blank lines, found 0
    E302
max-line-length = 99
```

Your .py files should now be linted on save. 

To have changed files lint automatically, enable auto-save on Visual Studio Code
`File > Auto Save`
