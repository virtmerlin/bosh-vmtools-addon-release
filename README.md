## BOSH VMware Packaged Tools Addon Release

Replaces open-vmtools with VMware's packaged VMwareTools on a given BOSH deployment:

**PIVOTAL DOES NOT OFFICIALLY SUPPORT REPLACING THE ```open-vmtools```.  Use at your own risk.

- No Arguments avail in version 0.0.1
- Will remove open-vmtools
- Will install|upgrade VMware Tools

## Usage

Only Intended to be used as a Bosh Addon

**1** Download the latest bosh release

```
wget https://github.com/virtmerlin/bosh-vmtools-addon-release/releases/download/0.0.1/bosh-vmtools-addon-release-0.0.1.tgz
```

**2** Upload the release to bosh

```
bosh upload release bosh-vmtools-addon-release-0.0.1.tgz
```

 
**3** Create Addon Yaml ```addon.yml```

```
releases:
  name: bosh-vmtools-addon-release
  version: 0.0.1
  
addons:
- name: vmtools
  jobs:
  - name: update-vmtools
    release: bosh-vmtools-addon-release
```

**4** Update the bosh runtime-config.  More Info can be found here [Runtime Config](https://bosh.io/docs/runtime-config.html)

```
bosh update runtime-config addon.yml
```

**5** The addon will apply to any new Jobs deployed by bosh.  You must recreate jobs on pre-existing deployments in order for the addon to be processed.

Possible actions to take:

```
bosh recreate [job] [index]
```

or 

```
bosh deployment [deployment.yml]
bosh deploy
```
 
