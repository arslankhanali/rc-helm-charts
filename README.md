# Chart Release cr
Instructions here: https://github.com/helm/chart-releaser

#### Installation
``` sh
cd /tmp
curl -sSL https://github.com/helm/chart-releaser/releases/download/v1.6.0/chart-releaser_1.6.0_darwin_amd64.tar.gz | tar xzf -
mv cr ~/bin/cr
```

#### Create pages branch
``` sh
git checkout --orphan gh-pages
git checkout gh-pages

cr package charts/{rbac,other}
```
#### cat $HOME/.cr.yaml
``` sh
owner: arslankhanali
git-repo: my-helm-charts
index-path: .
token: <>
```
#### For new charts and release
In main branch
``` sh
cr package charts/rbac
cr upload --packages-with-index --config $HOME/.cr.yaml --push --skip-existing
cr index --packages-with-index  --config $HOME/.cr.yaml --push

# Upload new release in .cr-release-packages/
git add .
git commit -am "New Release"
git push
```

####