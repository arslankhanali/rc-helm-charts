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
cd Codes/my-helm-charts
cr package charts/rbac
cr upload  --config $HOME/.cr.yaml --push --skip-existing
cr index   --config $HOME/.cr.yaml --push

# Upload new release in .cr-release-packages/
git add .
git commit -am "New Release"
git push
```
In gh-pages branch: index.yaml file will be automatically updated and new tar release will be uploaded.

# Home

# Helm Chart Repository

[rbac](https://github.com/arslankhanali/my-helm-charts/tree/main/charts/rbac)
[s2i](https://github.com/arslankhanali/my-helm-charts/tree/main/charts/s2i)

## Usage

Install helm on your machine using the [official docs](https://helm.sh/docs/intro/install/)

```shell
helm repo add arslankhanali https://arslankhanali.github.io/my-helm-charts/
```
```shell
helm repo update
```
```shell
helm search repo arslankhanali
```
```shell
helm install rbac arslankhanali/rbac
```

```shell
helm uninstall rbac
```