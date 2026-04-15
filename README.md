# Files

- `extension.ts` what previously used to be `index.ts`
- `details.ts` kind of behaves like vite's `vite.config.ts` file, where it is a typescript file that is expected to be executed locally to undertsand the 'config' of your system. Results in the production of `details.json` file that determines the extension menu display information of an extension

# Some new ideas

- `build` script should produce a zip archive that contains the following files: `extension.js`, `details.json` (and could optionally have an `auxiliary.js` file for things like any bundled UI elements)
  - That zip archive will be named with the extension id, e.g. `my-extension.zip`
  - must then updated both:
    - vm extension loader: should  
    - gui extension menu: must be updated to read some file that lists all available extension zips (e.g. `extensions.json`), and then load the details for each extension from the zip file itself (e.g. from `details.json` inside the zip)
    - NOTE: This can be implemented ON TOP of the current system, so that we can incrementally update things

# It SHOULD BE possible...

- to co-develop extensions, i.e. we might have a repo that has multiple extensions co-located. The file structure might look like:
- doodlebot/
  - package.json
  - basic/
    - extension.ts
    - details.ts
  - line-following/
    - extension.ts
    - details.ts
  - conversation/
    - extension.ts
    - details.ts
- to levereage a LOCAL version of the scratch-packages with the `dev` script, so that we could co-develop some vm-things along with an extension. Might look like:
  - example-extension/
    - package.json
    - extension.ts
    - details.ts
    - scratch-editor/
      - .gitrepo
      - scratch-gui/*
      - scratch-vm/*
  - NOTE: In this case, we should actually leverage the webpack dev-server for the scratch side so that as we make changes to the vm or the gui, things reload