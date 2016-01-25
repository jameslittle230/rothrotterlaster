# <http://rothrotterlaster.com>

A website for Drs. Roth, Rotter, and Laster in Brookline, MA

This website uses Jekyll as a templating tool and SCSS as a stylesheet
preprocessor, so it needs to be compiled to be visible. The SCSS and Jekyll
compilation processes are separate: SCSS is compiled in the development machine,
while Jekyll is compiled on the server. Here's the workflow:

## Setting up the Dev machine

The development machine is my local computer (for now). On it, I have the
latest version of [Ruby](https://www.ruby-lang.org/en/) through [RVM](http://rvm.io).
Installation instructions for Ruby and RVM were found [on this Github repository](https://github.com/nicolashery/mac-dev-setup);
the relevant portions are below:

> When installing Ruby, best practice is to use [RVM](https://rvm.io/) (Ruby
> Version Manager) which allows you to manage multiple versions of Ruby on the
> same machine. Installing RVM, as well as the latest version of Ruby, is very
> easy. Just run:
>
> ```bash
> curl -L https://get.rvm.io | bash -s stable --ruby
> ```
>
> When it is done, both RVM and a fresh version of Ruby 2.0 are installed. The
> following line was also automatically added to your `.bash_profile`:
>
> ```bash
> [[ -s "$HOME/.rvm/scripts/rvm" ]] && source "$HOME/.rvm/scripts/rvm"
> ```

From there, the software [Jekyll](http://jekyllrb.com) must be installed.
Because RVM comes with its own installation of `gem`, the Ruby package manager,
we do not need to use `sudo` commands to install Jekyll. Instead, just run

```bash
gem install jekyll
```

Now, Jekyll is installed; you can run `jekyll -v` to make sure.

Next, you'll want to make sure [Sass](http://sass-lang.com) is installed. I'm
not sure if Jekyll installs a copy of Sass as a dependency, but you can check
by running `sass -v`. If that comes up with a version number, you should be
good, but if it doesn't, run

```bash
gem install sass
```

to get Sass installed.

## Development

You need to have two or three terminal tabs running to compile the website; two
if you're using a GUI for Git, three if you're using Git on the terminal. The
first tab will be where the Jekyll source is compiled. Navigate to the website's
directory and run

```bash
jekyll serve
```

This will watch the folder for any file changes and compile the site if it sees
any. The site gets compiled into the `_site` directory, which is served on a
local server. When you visit <http://localhost:4000> in your browser, Jekyll
should be serving a compiled version of your site.

The second tab will be where you compile your Sass code. Navigate to the
`styles` directory and run

```bash
sass --watch main.scss:main.css
```

This will watch the file `main.scss` and its dependencies for any changes, and
compile them into `main.css` when they are found.

## A note on Git

Make sure you're committing often. A good commit history helps all the changes
be better understood. With this site, I'm trying to use Github Flow,
