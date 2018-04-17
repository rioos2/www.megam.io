docs.rioos.xyz
==============

This is the documentation repository for Rio OS => http://rio.digital/docs


The documentation is [live here](https://agitated-lalande-9effd8.netlify.com/)


The `rioos.xyz` is a temp domain for engineering to easy identification and separation only.

## Hosted

At the moment this is hosted in netlify.com. 

A push to this repository will refresh documentation automatically. 

Login to netlify [app.netlify](https://app.netlify.com)

Userid: **kishore.neelamegam@netlify.com**
Password: **Team#4rio**

## Updating documentation locally

**These instructions are tested in Linux and FreeBSD**

1. Install  Ruby 2.5.1 via rvm.io or anyothers


2. Fork & clone this repository to your id (eg: paulsanar)

```

git clone https://gitlab.com/paulsanar/docs.rioos.xyz

cd docs.rioos.xyz

git remote -v

git remove rm origin

git remote add origin https://gitlab.com/rioos/docs.rioos.xyz
git remote add master https://gitlab.com/paulsanar/docs.rioos.xyz


```

3. Install bundler

```

gem install bundler

```

4. Run jekyll, and start editing using your favourite editor (atom.io, vscode, sublimetext or any others)

```
bundle install 


jekyll clean

jekyll serve

```

5. Edit files using markdown (.md) 

[Local changes are in url](http://127.0.0.1:4000)


6. When you are happy push to your repo

```

git add .

git commit -m "Updated sections ..."

git push master

```

7. Provide a merge request from your `paulsanar` to `rioos`


8. When the pull request is merged, the docs get refreshed [live here](https://agitated-lalande-9effd8.netlify.com/)






