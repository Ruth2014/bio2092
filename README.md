# bio2092
Computer practical materials for Genomics &amp; Introductory Bioinformatics course (BIO2092) at the University of Exeter
# Skeleton workshop

This is a sample workshop, i.e. a skeleton you can use to add your own content. 

As it's markdown based, adding content is pretty painless, especially if you already have content 
saved as markdown. 

Alternatively you can also add static HTML if you wish. 

If you have workshop notes in some other format, [Pandoc](https://pandoc.org/)
is an **excellent tool** for converting between formats.

## To create a new course repository
First create an empty repository under the biomedicalhub github account, then:

```
# clone your new directory locally.
git clone git@github.com:biomedicalhub/my-new-repository.git
cd my-new-repository

# add skeleton as a remote
git remote add skeleton git@github.com:biomedicalhub/skeleton.git

# create a gh-pages brach and pull in the skeleton files
git checkout -b gh-pages
git fetch skeleton/gh-pages
git merge --allow-unrelated-histories  skeleton/gh-pages

# remove the skeleton remote
git remote remove skeleton
```
