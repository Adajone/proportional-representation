# proportional-representation
1. Get data ✅
   - Got from https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/42MVDX where it is posted under
https://creativecommons.org/publicdomain/zero/1.0/
   - See src/data/dataverse_files/README.md for more info
   - Need Electoral college votes by state by year
      - https://www.270towin.com/state-electoral-vote-history/#google_vignette
2. Find USA state graph creator (JS) ✅
   - Can be done with ObservableHQ Plot
   - https://observablehq.com/@observablehq/plot-us-map
3. Make JS code for proportional representation
4. Make webpage with by-year lookup
5. Host on GH Pages ✅
   - yoinked from https://notes.billmill.org/programming/observable_framework/github_workflow_for_publishing_an_observable_framework.html
   - View it here! https://adajone.github.io/proportional-representation/


## Things we need to do:
- Make USA map ✅
- Make red-blue map for last election ✅
- Make input to change year
- Make proportional representation map for last election
- Make proportional representation map for all elections
- Make main page pretty
  - Title should have red-white-blue gradient
- Make electoral college vote bar above
- Handle states with split electoral votes
- Add postal code to data set

## Readme from Obserable Framework Starter App
#### Porportional Representation

This is an [Observable Framework](https://observablehq.com/framework) app. To start the local preview server, run:

```
yarn dev
```

Then visit <http://localhost:3000> to preview your app.

For more, see <https://observablehq.com/framework/getting-started>.

##### Project structure

A typical Framework project looks like this:

```ini
.
├─ src
│  ├─ components
│  │  └─ timeline.js           # an importable module
│  ├─ data
│  │  ├─ launches.csv.js       # a data loader
│  │  └─ events.json           # a static data file
│  ├─ example-dashboard.md     # a page
│  ├─ example-report.md        # another page
│  └─ index.md                 # the home page
├─ .gitignore
├─ observablehq.config.js      # the app config file
├─ package.json
└─ README.md
```

**`src`** - This is the “source root” — where your source files live. Pages go here. Each page is a Markdown file. Observable Framework uses [file-based routing](https://observablehq.com/framework/routing), which means that the name of the file controls where the page is served. You can create as many pages as you like. Use folders to organize your pages.

**`src/index.md`** - This is the home page for your app. You can have as many additional pages as you’d like, but you should always have a home page, too.

**`src/data`** - You can put [data loaders](https://observablehq.com/framework/loaders) or static data files anywhere in your source root, but we recommend putting them here.

**`src/components`** - You can put shared [JavaScript modules](https://observablehq.com/framework/javascript/imports) anywhere in your source root, but we recommend putting them here. This helps you pull code out of Markdown files and into JavaScript modules, making it easier to reuse code across pages, write tests and run linters, and even share code with vanilla web applications.

**`observablehq.config.js`** - This is the [app configuration](https://observablehq.com/framework/config) file, such as the pages and sections in the sidebar navigation, and the app’s title.

##### Command reference

| Command           | Description                                              |
| ----------------- | -------------------------------------------------------- |
| `yarn install`            | Install or reinstall dependencies                        |
| `yarn dev`        | Start local preview server                               |
| `yarn build`      | Build your static site, generating `./dist`              |
| `yarn deploy`     | Deploy your app to Observable                            |
| `yarn clean`      | Clear the local data loader cache                        |
| `yarn observable` | Run commands like `observable help`                      |
