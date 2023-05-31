# Frontend development

## Tools 
  - VSCODE
     - Extensions
        - Prettier
        - ESlint
        - in VSCode settings.json set  
        `"editor.defaultFormatter": "esbenp.prettier-vscode",
         "editor.formatOnPaste": true,
         "editor.formatOnSave": true
        `
    - Useful shorcuts(windows)
      - ctl + ` - opens/closes terminal
      - ctl + p - search files by name
      - ctl + g - navigate to line in code
      - ctl + d - selects next occurency of selected text / alt + c matches selected case
      - ctl + f - search contents in file, ctl + shift + f search the whole repository
      - ctl + h - find and replace
      - ctl + [ or ] folds and unfolds specific code
      - for more shorcuts check https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
      - Note  
      If the whole devs folder is opened, VSCode might complain about too many files to watch  
      ` "files.watcherExclude": {
         "**/.git/objects/**": true,
         "**/.git/subtree-cache/**": true,
         "**/node_modules/**": true,
        "**/samples": true
        }
       `  
      should fix the warning
## Setup
 - Structure of webui bundle:
   - bundle
      - webapp - it is created on every make/build, should always go to gitignore
      - bundle.properties
      - extensions.xml
   - web-src - code for creating React/Vite app goes in here, difference from the standard setup  
     `
      "build": "vite build --outDir ../bundle/webapp --base [bundle path set in extensions.xml] "
      `
   - [Name of the bundle].bndlspec
   - Makefile
