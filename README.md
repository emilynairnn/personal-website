# Vue Personal Website Template

This site is built with Vue centric JAM stack technologies and pre-rendered. All content is served over the Netlify CDN as static HTML.

## Tech Stack
- [Vue](https://vuejs.org/): Javascript framework
- [Vuetify](https://vuetifyjs.com/en/): Responsive material design component
- [Nuxt](https://nuxtjs.org/): Static HTML generation
- [Github](https://docs.github.com/en/graphql): GraphQL API
- [Medium](https://medium.com/): Serverless API for blog entries
- [Google Fonts](https://fonts.google.com/): Web fonts via CSS
- [Netlify](https://www.netlify.com/): Hosting, forms, CI/CD
- [Content](https://content.nuxtjs.org/): Markdown based CMS

## Setup
### Github Access

To access github information, you will need to create a github access token. [You can read how to do that here](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).

Once you have your token generated, create the file `.env` in the /src folder that contains the following.

```
GITHUB_API_TOKEN=<Paste your token here>
```

To have your site build in the cloud by a Github action or other CI/CD tool, save Github access token as an environment variable in the web interface. [Here are instructions to set up environment variables in Netlify (scroll down a little).](https://www.netlify.com/blog/2020/12/10/environment-variables-in-next.js-and-netlify/)


### Build Setup

```bash
# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
