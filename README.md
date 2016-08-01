[![license](https://img.shields.io/github/license/plus3it/splunkforwarder-formula.svg)](./LICENSE)
[![Travis-CI Build Status](https://travis-ci.org/plus3it/splunkforwarder-formula.svg)](https://travis-ci.org/plus3it/splunkforwarder-formula)
[![AppVeyor Build Status](https://ci.appveyor.com/api/projects/status/github/plus3it/splunkforwarder-formula?branch=master&svg=true)](https://ci.appveyor.com/project/plus3it/splunkforwarder-formula)

# splunkforwarder-formula

Salt formula to install and configure the Splunk Universal Forwarder. This
formula supports both Windows and Linux.

On Windows, the formula depends on the Salt Windows Package Manager (`winrepo`),
and a `winrepo` package definition must be present for the Splunkforwarder.
Configuring `winrepo` is not handled by this formula.

## Available States

-   [splunkforwarder](#splunkforwarder)

### splunkforwarder

Install and configure the Splunk Universal Forwarder.

## Windows Configuration

This formula requires configuration via pillar. If the required parameters are
not configured in pillar, the formula will fail.

### (Windows) splunkforwarder:lookup:deploymentclient

This parameter is a map containing the `source` and `source_hash` of the
deploymentclient.conf file.

>**Required**: `True`

**Example**:

```yaml
splunkforwarder:
  lookup:
    deploymentclient:
      source: https://path/to/my/deploymentclient.conf
      source_hash: https://path/to/my/deploymentclient.conf.HASH
```

### (Windows) splunkforwarder:lookup:log_local

This parameter is a map containing the `source` and `source_hash` of the
log-local.cfg file.

>**Required**: `True`

**Example**:

```yaml
splunkforwarder:
  lookup:
    log_local:
      source: https://path/to/my/log-local.cfg
      source_hash: https://path/to/my/log-local.cfg.HASH
```

### (Windows) splunkforwarder:lookup:package

The `package` parameter is the name of the package as defined in the winrepo
package definition.

>**Required**: `False`
>
>**Default**: `splunkforwarder`

**Example**:

```yaml
splunkforwarder:
  lookup:
    package: splunkforwarder
```

### (Windows) splunkforwarder:lookup:service

The `service` parameter is the name of the Windows service for the Splunk
Universal Forwarder.

>**Required**: `False`
>
>**Default**: `SplunkForwarder`

**Example**:

```yaml
splunkforwarder:
  lookup:
    service: SplunkForwarder
```

## Linux Configuration

This formula requires configuration via pillar. If the required parameters are
not configured in pillar, the formula will fail.

### (Linux) splunkforwarder:lookup:package_url

This parameter is the URL to the RPM package for the Splunk Universal
Forwarder. The formula will use this RPM to install the splunkforwarder.

>**Required**: `True`

**Example**:

```yaml
splunkforwarder:
  lookup:
    package_url: https://path/to/my/splunkforwarder.rpm
```

### (Linux) splunkforwarder:lookup:deploymentclient

This parameter is a map containing the `source` and `source_hash` of the
deploymentclient.conf file.

>**Required**: `True`

**Example**:

```yaml
splunkforwarder:
  lookup:
    deploymentclient:
      source: https://path/to/my/deploymentclient.conf
      source_hash: https://path/to/my/deploymentclient.conf.HASH
```

### (Linux) splunkforwarder:lookup:log_local

This parameter is a map containing the `source` and `source_hash` of the
log-local.cfg file.

>**Required**: `True`

**Example**:

```yaml
splunkforwarder:
  lookup:
    log_local:
      source: https://path/to/my/log-local.cfg
      source_hash: https://path/to/my/log-local.cfg.HASH
```

### (Linux) splunkforwarder:lookup:package

The `package` parameter is the name of the package as defined in the RPM
provided to the `package_url` parameter.

>**Required**: `False`
>
>**Default**: `splunkforwarder`

**Example**:

```yaml
splunkforwarder:
  lookup:
    package: 'splunkforwarder'
```

### (Linux) splunkforwarder:lookup:service

The `service` parameter is the name of the Linux service for the Splunk
Universal Forwarder.

>**Required**: `False`
>
>**Default**: `splunk`

**Example**:

```yaml
splunkforwarder:
  lookup:
    service: splunk
```