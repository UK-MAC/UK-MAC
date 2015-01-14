# Guide to UK-MAC

The UK-MAC repo is a top level collection of mini-apps from the [UK-MAC](http://uk-mac.github.io) page.
Downloading this repo will result in a copy of all of the released mini-apps.

These are made available via git submodules.

Each submodule points to a top level github repo for the specific mini-app.

```
               UK-MAC
              /      \
            /          \         
      CloverLeaf       TeaLeaf
     /         \       /     \
   Ref     OpenACC    Ref    OpenCL

```

These submodules point to a specific release of the mini-app.
These should be controlled with tags

##  Tagging a code

Upon a release a code should be tagged, to provide a reference point.
The tagging convention is `vx.x.x`.

This can be done in git after pushing the commit of the release.

```
git commit -am "Final modifications for release"
git push
git tag "v1.1.1"
git push --tags
```

This will make sure that the correct tag is applied to the version.

Now the containing repos need updating.
This will apply for all containers, e.g. for CloverLeaf_ref then CloverLeaf and UK-MAC need updating. 


## Updating a submodule

Say we have just release a version "v1.1.1" of CloverLeaf_ref, we now go to the CloverLeaf repo and update the submodule:

```
git clone --recursive https://github.com/UK-MAC/CloverLeaf.git
cd CloverLeaf/CloverLeaf_ref
git pull origin master
git cd ../
git commit -am "Updated CloverLeaf ref to v1.1.1"
git push
```

If this is a big change then it would be wise to tag the CloverLeaf repo too.

### Update all submodules

To do this for all submodules in a repo:
```
git submodule foreach git pull origin master
git commit -am "Updated all submodules"
git push
```


### Update to a specific version

Simply doing a `pull origin master` will update to the current head of the repo.
To update to a specific tag you must checkout the tag within the submodule:

```
git clone --recursive https://github.com/UK-MAC/CloverLeaf.git
cd CloverLeaf/CloverLeaf_ref
git pull origin master
git checkout "v1.1.1"
git cd ../
git commit -am "Updated CloverLeaf ref to v1.1.1"
git push
```

## Setting up web page

See: [Github Guide](https://help.github.com/articles/creating-project-pages-manually/)

# Push Branch to new Repo

Make the new repo on the GitHub webpage.

Clone the branch locally and checkout the correct branch e.g. <3d>.
To push to new repo - as a master branch e.g. TeaLeaf3D_ref.

```
git push git@github.com:UK-MAC/TeaLeaf3D_ref +3d:master
```

