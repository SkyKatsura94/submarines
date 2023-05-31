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
    - Useful shortcuts(windows)
      - ctl + ` - opens/closes terminal
      - ctl + p - search files by name
      - ctl + g - navigate to line in code
      - ctl + d - selects next occurency of selected text / alt + c matches selected case
      - ctl + f - search contents in file, ctl + shift + f search the whole repository
      - ctl + h - find and replace
      - ctl + [ or ] folds and unfolds specific code
      - for more shortcuts check https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf
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
  - Postman for API testing
  - React developer tools for debugging from browser - https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi
## Setup
 - Structure of webui bundle:
   - bundle
      - webapp - it is created on every make/build, should always go to gitignore
      - bundle.properties
      - extensions.xml
   - web-src - code for creating Vite(React) app goes in here, the difference from the standard setup in package.json set build dir to webapp
     `
      "build": "vite build --outDir ../bundle/webapp --base [bundle path set in extensions.xml] "
      `
     - src important folders
        - constants - used for storing relative paths to APIs  and services ex: `export const BASE_SESSION_PATH = "/macchina/session.json";`
        - css
        - js
   - [Name of the bundle].bndlspec
   - Makefile
## Workflow
  - After every change in  web-src execute
    `make clean && make` in Webui bundle folder 
  - Setup for working live
    - Change all relative paths in your web-src to absolute paths BASE_SESSION_PATH = "/macchina/session.json";` -> http://localhost:22080/macchina/session.json
    - Run macchina from command line (./runDevs.sh or ./runApps/sh)
    - Login
    - In a separate terminal, execute npm run dev from web-src folder, the default port is 5173
    - In another tab open localhost:5173 and every change from now on should be reflected in the browser in real time
    - If having issues with CORS, `chromium --disable-web-security --user-data-dir="."` should allow you to work
   
