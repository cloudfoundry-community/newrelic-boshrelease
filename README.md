# BOSH Release for newrelic server monitor

## Usage

To use this bosh release, first upload it to your bosh:

```
bosh target BOSH_HOST
git clone https://github.com/cloudfoundry-community/newrelic-boshrelease.git
cd newrelic-boshrelease
bosh upload release releases/newrelic/newrelic-3.yml
```

Then add the newrelic license to the properties section of your manifest file and the newrelic release to the releases section:

```
properties:
  ...
  newrelic:
    license_key: foobar
releases:
- ...
- name: newrelic
  version: latest
```

Finally add the `newrelic-monitor` template to your job:

```
- instances: 1
  name: runner_z1
  ...
  templates:
  - ...
  - name: newrelic-monitor
    release: newrelic
```
