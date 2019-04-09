# CosmicBagel Blog Repo

[![Netlify Status](https://api.netlify.com/api/v1/badges/36c74e3a-8453-4eb4-9b86-dff0fe7fcd6e/deploy-status)](https://app.netlify.com/sites/cosmicbagel/deploys)

- Github repo for my rarely updated blog
- Auto deploys to netlify static host
- CSS is generated using nodejs stuff

#### Notes to future me since you'll forget
- Using hugo 0.53, I guess you can update this if you need to, but eh
  - [Download](https://github.com/gohugoio/hugo/releases/tag/v0.53)
- Just run `hugo server` while developing, you put hugo into your Tools folder, you already added it to the PATH variable (unless you on new comp, in which case where tf did you get the money for that)
- Using `--minify` in the netlify just cuz, idk if it makes that big of a difference, but why not
- If you're changing the CSS,run `grunt` or `grunt watch` in the `themes/hyde-y` folder, asuming you have all the node prereqs installed
- Site still requires JS to display the header icon links, should look into removing that requirement
- Look into using this https://www.netlify.com/products/dev/


