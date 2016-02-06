## picnicman.com

picnicman.com is statically generated using `jekyll`.

## Environments ##

Production, via CloudFlare
http://www.picnicman.com/

Production, direct to S3
http://www.picnicman.com.s3-website-us-east-1.amazonaws.com/

## Prerequisites ##

Using MacOS and Homebrew:

    # install ruby and optional libraries for html-proofer
    brew install libyaml openssl gdbm gmp libffi ruby

    # install bundler
    gem install bundler

If you plan to deploy manually:

    # install awscli
    brew install awscli

and be sure to configure your aws credentials.

## Setup ##

    # clone repo
    git clone git@github.com:jefforulez/picnicman.git

    # change working directory
    cd ./picnicman

    # install gems
    bundle install

    # start local server
    bundle exec jekyll serve

Site will be viewable at http://127.0.0.1:4000/

## Deployment ##

### CircleCI ###

CircleCI handles deploying to staging and production.

* Commits to `master` are deployed to production

### Manual ###

Manual deployment requires that `awscli` is installed and that you have aws credentials
that allow you to write to `s3://www.picnicman.com/`.

    # build the site
    JEKYLL_ENV=production bundle exec jekyll build

    # test the site
    bundle exec htmlproof ./_site

    # sync to production
    aws s3 sync _site s3://www.picnicman.com/

## Related ##

* Bundler -- http://bundler.io/
* jekyll -- https://jekyllrb.com/
* HTML::Proofer -- https://github.com/gjtorikian/html-proofer
