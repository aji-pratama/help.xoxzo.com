# README
Xoxzo's Help Center

This document serves as a quick guide and reminder on how to work with Xoxzo's
help center using Markdown and Pelican.

## Quickstart

### Preparing your environment

    virtualenv -p python3.4 venv
    source venv/bin/activate
    pip install -r requirements.txt
    make build

### Creating the html

After preparing your environment, you can create contents by creating .md files
in the content directory. Before you start working, pull the latest from GitHub
first:

    git pull origin master

Once you've written your articles,

    make html
    make serve
    OR 
    make devserver # that will do make html and make serve

and access *localhost:8000* via your browser to make sure everything looks ok.

### Pushing to GitHub

If everything looks good, commit and push it to GitHub:

    git add <file>
    git commit
    git push origin master
    make github

## Writing contents

### Filename

Please follow the format of the filenames that you see, i.e append the language
at the end of the file name after the filename itself:

    合計 16
    drwxr-xr-x  2 iqbal iqbal 4096 12月 19 09:23 .
    drwxrwxr-x 12 iqbal iqbal 4096 12月 28 20:43 ..
    -rw-rw-r--  1 iqbal iqbal 1221 12月 17 21:17 end-of-kof-en.md
    -rw-rw-r--  1 iqbal iqbal 1166 12月 17 21:17 end-of-kof-ja.md

### Category

Categories are decided by the directory which you have your .md files in. Basically
this means we'll want only one category for an article, so choose carefully
which category your article can be in and only create a new directory (category)
when there are no suitable categories.

If you want to connect your article to different topics, use the Tags metadata
instead.

### Metadata

These metadata is required for all articles

    Title: 
    Date: 
    Author: 
    Tags: 
    Slug: 

#### Translations

It is mandatory to specify **Lang** metadata for each article,
like this:

    Title: Participating KOF-Kansai Open Source Forum
    Date: 2016-11-14 11:00 
    Slug: kof-2016-report
    Lang: en
    Modified: 2012-11-14 11:00
    Tags: kof; osaka; exhibition;
    Author: Aiko Yokoyama
    Summary: We participated in the KOF 2016 and this is what we think

#### Theme Translations
To translate string in templates, make the string translatable:

    {% trans %}Who we are ?{% endtrans %}

Then run:

    make pot_translation

This will create translation file in `locales/ja/LC_MESSAGES/messages.po`. Translate
the string and then run:
    
    make compile_translation
    make html
