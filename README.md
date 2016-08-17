# tibet-search
The TIBET git repo must be present in a directory named ./TIBET within this repo.
The TIBET app must be named 'hello' and in a directory named ./hello within this repo.

Neither of these directories are included in this repo.  They must be added prior to building the image.

ejabberd is installed and running

This currently offers not only a [CouchDB 2.0](http://couchdb.apache.org/) but also additional IBM Cloudant search capabilities that follow the steps from this [blog post](https://cloudant.com/blog/enable-full-text-search-in-apache-couchdb/#.Vly24SCrQbV) from [Cloudant](https://cloudant.com/).

## Prerequisites
You need to have a recent version of [Docker](https://www.docker.com/) installed

## Executing the Stack

Build the image from the Dockerfile and run using the following:
```
docker build --tag="tibet_jabber_fauxton_couchdb" ${PWD}
docker run -p 1407:1407 -p 15222:15222 -p 15269:15269 -p 15984:15984 tibet_jabber_fauxton_couchdb
```

There will be a Fauxton console available at http://localhost:15984/_utils, TIBET 'hello' app at http://localhost:1407 and ejabberd service at 15222 and 15269

Full text searching is enabled and fully functional.  See the Cloudant [documentation](https://cloudant.com/for-developers/search/) for more info on how to test use the full text searching capabilities.

## Running tests
It uses [Serverspec](http://serverspec.org/) to test the Dockerfile:
```
$ bundle
$ bundle exec rspec
```
