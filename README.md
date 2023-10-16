# Nocsys Helm Charts

## Add new helm charts by submodule
1. Put new charts into charts, ex:
```
cd charts/
git submodule add {url-of-repo} {chart-name}
git commit
```

## Update helm charts by submodule
1. Update submodule under charts, ex:
```
cd charts/{chart-name}
git checkout {commit-id}
cd ..
git add charts/{chart-name}
git commit
```

## Update helm-flowpipe
1. checkout specified version of goflow2
```
cd goflow2
git checkout {commit-id}
```
2. update symbolic link to goflow2/helm
```
cd charts
rm helm-flowpipe-{old-ver}
ln -s ../goflow2/helm helm-flowpipe-{new-ver}
git add .
git commit
```

---

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

```console
helm repo add nocsys https://nocsyshelmrepo.github.io/nocsys-helm-chart
```

If you had already added this repo earlier, run `helm repo update` to retrieve the latest versions of the packages.

You can then run `helm search repo nocsys` to see the charts.

