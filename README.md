## Peter Schaadt's Web Site

This site is compiled by [Octopress](http://octopress.org), a framework for [Jekyll](https://github.com/mojombo/jekyll).

### Documentation

Install Ruby 1.9.2 with [RVM](https://rvm.io)

```
rvm install 1.9.2 && rvm use 1.9.2
```

Install Jekyll

```
gem install jekyll
```

Create a new page

```
rake page name="about/index.md"
```

Create a new post

```
rake post title="Hello World"
```

Generate Jekyll posts and pages and copy to public directory

```
rake generate
```

Watch /source and /sass for changes, then regenerate

```
rake watch
```

Watch and mount webserver

```
rake preview
```

Run the Jekyll server

```
jekyll --server
```

View site at http://localhost:4000
