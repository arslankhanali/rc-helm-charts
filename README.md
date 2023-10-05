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
git-repo: rc-helm-charts
index-path: .
token: <>
```
#### For new charts and release
In main branch
``` sh
# Upload new release in .cr-release-packages/
cd Codes/rc-helm-charts
git add .
git commit -am "New Release"
git push

cr package charts/s2i
cr upload  --config $HOME/.cr.yaml --push --skip-existing
cr index   --config $HOME/.cr.yaml --push


```
In gh-pages branch: index.yaml file will be automatically updated and new tar release will be uploaded.

# Home

# Helm Chart Repository

[rbac](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/rbac)
[s2i](https://github.com/arslankhanali/rc-helm-charts/tree/main/charts/s2i)

## Usage

Install helm on your machine using the [official docs](https://helm.sh/docs/intro/install/)

```shell
helm repo add rc-helm-charts https://arslankhanali.github.io/rc-helm-charts/
```
```shell
helm repo update
```
```shell
helm search repo rc-helm-charts
```
```shell
helm install rbac rc-helm-charts/rbac
```

```shell
helm uninstall rbac
```