( using the directions found here: http://chrisknightindustries.com/2015/24/11/git-subtrees-for-trellis-workflow.html )

$ mkdir new_roots_project

$ git init

$ git remote add origin { add your repo here }

( create a .gitignore and add your first commit )

## ADD TRELLIS

$ git remote add trellis https://github.com/roots/trellis.git

$ git fetch trellis

$ git checkout -b trellis trellis/master

$ git checkout master

$ git read-tree --prefix=trellis/ -u trellis/master

$ git commit -m "add trellis subtree"

## ADD BEDROCK

$ git remote add bedrock https://github.com/roots/bedrock.git

$ git fetch bedrock

$ git checkout -b bedrock bedrock/master

$ git checkout master

$ git read-tree --prefix=site/ -u bedrock/master

$ git commit -m "add bedrock subtree"

## ADD SAGE

$ git remote add sage https://github.com/roots/sage.git

$ git fetch sage

$ git checkout -b sage sage/master

$ git checkout master

$ git read-tree --prefix=site/web/app/themes/sage -u sage/master

$ git commit -m "add sage subtree"

## UPDATING

$ git checkout trellis

$ git pull

$ git checkout master

$ git merge --squash -s subtree --no-commit trellis

$ git commit -m "update trellis from trellis/master"