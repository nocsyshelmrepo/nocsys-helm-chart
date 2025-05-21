# Nocsys Helm Charts

## Add new helm charts by submodule

There are three situations to add new submodule:
1. Helm Chart Files Directly in the Root Folder. For example: [helm-yolo](https://github.com/nocsyshelmrepo/helm-yolo)  
   Put new charts into charts/, ex:
   ```
   cd charts/
   git submodule add {url-of-repo} {chart-name}
   git commit
   ```

2. Helm Chart Files in a Subfolder. For example: [goflow2](https://github.com/nocsysmonitor/goflow2/tree/2716cd03f5a4289d837dcae92b3b5a20a274ba86)  
   First, link to the repository, then add a link to the helm chart files within it.
   ```
   git submodule add {url-of-repo} {chart-name}
   cd charts
   ln -s ../{chart-name}/{helm-chart-locations} {chart-name}-{version}
   git commit
   ```

3. Helm Chart is not in a traditional format. For example: [jupyterhub](https://github.com/jupyterhub/zero-to-jupyterhub-k8s). Jupyterhub helm files are stored as `.tgz` archives in the `gh-pages` branch.  
   ```
   git submodule add {url-of-repo} {chart-name}
   cd {chart-name}
   git checkout {commit-id}
   cd ..
   cd charts
   ln -s ../{chart-name}/{helm-chart-locations} {chart-name}-{version}
   git commit
   ```  
   
Once changes are merged into `main` branch of `nocsys-helm-chart` and Actions complete, the `index.yaml` in `gh-pages` branch will be updated automatically.  

## Update helm charts by submodule
1. Update submodule under charts/, ex:
```
cd charts/{chart-name}/
git checkout {commit-id}
cd ..
git add charts/{chart-name}
git commit
```

## Update helm-flowpipe
1. Checkout specified version of goflow2, ex:
```
cd goflow2
git checkout {commit-id}
```
2. Update symbolic link in charts/, ex:
```
cd charts
rm helm-flowpipe-{old-ver}
ln -s ../goflow2/helm helm-flowpipe-{new-ver}
git add .
git commit
```

`Note: chart-releaser-action only detects changes in charts/ directoy.`

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
