# Overview

Process for creating snapshots of the OpenStack packages from upstream source.

# Create and import snapsnots

Examples given are for the Epoxy release; adapt for the current focus of
development.

```
for package in `cat current-projects`; do
    ./pkg-snapshot-version-git $package master epoxy
done
```

This will take a while - packages are places in the `pkg` subfolder.

# Push branches and tags to Launchpad

```
for package in `cat current-projects`; do
    (
        cd pkg/$package
        git push origin upstream-epoxy pristine-tar
        git push origin --tags
    )
done
```
