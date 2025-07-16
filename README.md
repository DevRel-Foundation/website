> [!IMPORTANT] 
> 🗂️Archived. New website being deployed in https://github.com/DevRel-Foundation/site

# The DevRel website

This repo houses the assets used to build the website for the [DevRel](https://dev-rel.org/) at https://dev-rel.org.

## 🧩 Editing the site

This site is built using the [Hugo](https://gohugo.io) static site generator and hosted on [Netlify](https://netlify.com). The site uses the [Dot-Org Theme for Hugo](https://github.com/cncf/dot-org-hugo-theme) as a base and then has its own customisations.

In order to build or locally develop the website, you'll need to install [Hugo](https://gohugo.io) and [node.js](https://nodejs.org/en).

If you don't have them installed, you can install them via [brew.sh](https://brew.sh).

```bash
# macOS
brew install hugo node
```

Then following these instructions:

1. Clone this repo to a local directory on your computer.

2. Navigate to the newly created directory, and pull in the theme:

```bash
git submodule update --init --recursive
```

3. Install dependencies:

```bash
npm install
```

4. Build the site:

```bash
npm run build
```

5. Start the local server with live reload:

```bash
npm run start
```

## Other npm commands for working with a local instance

- `npm run dev:start` - Starts the local dev environment using exampleSite
- `npm run dev:start:with-pagefind` - Starts the local dev environment using exampleSite with working pagefind search
- `npm run dev:build` - Builds the site using exampleSite

### To run in docker

As mentioned above, fork and clone this repository, run `git submodule update --init --recursive`, then run following:

```bash
./run-hugo-in-docker.sh
```

This command should give an address you can visit on your local machine to see the local copy of your site. Typically this is `localhost:1313`. Just navigate to http://localhost:1313 in your browser and you should see the site running.

If modifying the theme files, you should never edit the theme that is imported via Git Submodule, as otherwise the changes will be overwritten or lost the next time the theme is updated. Changes should be made in override files inside the root directory as this will override the theme directory. [Read docs](https://gohugo.io/getting-started/directory-structure/).

## Updating the theme

Some brief notes on how to update the theme:

From the site root:

```
git submodule init
git submodule update
cd themes/dot-org-hugo-theme
git fetch
git checkout main
git pull origin main
cd ../..
git add themes/dot-org-hugo-theme
git commit -m "Updated submodule to the latest version of dot-org-hugo-theme" -s
```
