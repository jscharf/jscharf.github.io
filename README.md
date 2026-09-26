# jscharf.github.io

Personal site and blog, built with Jekyll and published to GitHub Pages.

## Local development

Use the Ruby version in `.ruby-version`, then install the locked dependencies and start Jekyll:

```sh
bundle install
bundle exec jekyll serve
```

The site is available at <http://localhost:4000>. Run `bundle exec jekyll build` to build it without starting the development server.

## Publishing

Pushes to `master` are built and deployed to GitHub Pages by [the Actions workflow](.github/workflows/build.yml). Pull requests run the build without deploying.
