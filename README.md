# Some new ideas

- `build` script should produce a zip archive that contains the following files: `extension.js`, `details.json` (and could optionally have an `auxiliary.js` file for things like any bundled UI elements)
  - That zip archive will be named with the extension id, e.g. `my-extension.zip`
  - must then updated both:
    - vm extension loader: should  
    - gui extension menu: must be updated to read some file that lists all available extension zips (e.g. `extensions.json`), and then load the details for each extension from the zip file itself (e.g. from `details.json` inside the zip)
    - NOTE: This can be implemented ON TOP of the current system, so that we can incrementally update things