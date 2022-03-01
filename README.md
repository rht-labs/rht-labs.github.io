# Tech setup for the site

Below are instructions for how to set up a local development environment. Useful for when you want to make many changes and test locally before pushing to github.

## 1. Install GIT

Here's [how to install GIT](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

## 2. Clone this repo

You can choose to close this repo in two ways - **a)** using the upstream repo in read-only mode, or **b)** using a fork for full read/write access. Both methods are described below, but pick the one that fits your needs - if you are planning to submit contributions and PRs, make sure to use option **b)**.

### a. Using the upstream repo in read-only mode

Tell git to download the rht-labs.github.io source:

```bash
git clone https://github.com:rht-labs/rht-labs.github.io.git
cd rht-labs.github.io
```

### b. Using a fork for full read/write access

First, if you do not already have a github.com account, create one by [Signing up for a new GitHub Account](https://docs.github.com/en/get-started/signing-up-for-github/signing-up-for-a-new-github-account), then follow the [Adding a new SSH key to your GitHub acount](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) instructions to enable SSH access to your account. Next, follow the [Forking a repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository) instructions to create a fork of the upstream repo into your personal account. Lastly, follow the below instructions to clone the forked repo to your local laptop/device:

Tell git to download the rht-labs.github.io source from your fork - **make sure to replace _"my-username"_** with your github.com username:

```bash
export MY_GH_USERNAME=my-username
git clone git@github.com:${MY_GH_USERNAME}/rht-labs.github.io.git rht-labs.github.io.${MY_GH_USERNAME}
cd rht-labs.github.io.${MY_GH_USERNAME}
```


## 3. Working locally

You should now have the whole thing available locally on your laptop/device, including the README.md file that you are reading right now!

The web site source files are under `_docs`, have a look! They are written using [markdown](https://guides.github.com/features/mastering-markdown/) (a simpler format than html). When you push to github, it will automatically convert the pages to static html and build the site https://rht-labs.com/

## 4. Setup your Ruby Environment

First install Ruby if you don't already have it e.g.

```bash
# homebrew - http://brew.sh
brew install ruby

# fedora
dnf install -y ruby
```

Then install the Ruby Bundler gem, if you don't already have it.

```bash
sudo gem install bundler
```

Manage your ruby environments using [`rbenv`](https://github.com/rbenv/rbenv)

Install `rbenv`:

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

Set in your environment:

```bash
# ruby
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init - /bin/bash)"
```

Change your directory to this repository, and install the ruby environment - `rbenv` used by this repo's `.ruby-version`

```bash
rbenv install
```

## 5. Install Jekyll and related tools

Next, tell the bundler to install all the gems needed (jekyll, github-pages, etc). They are listed in Gemfile in case you are curious.

```bash
bundle install
```

If you are getting error messages, you may have old versions of some Gems installed. Try updating to the latest using:

```bash
bundle update
```

Congrats! You got the stuff you need. You should now be ready to....

## 6. Run the site locally!

Tell Jekyll to generate the site and serve it up:

```bash
jekyll serve
```

That's it, your local copy of the site should be up and running on
[http://localhost:4000](http://localhost:4000)

Every time you edit a source doc (under _docs) it will update the site automatically.
