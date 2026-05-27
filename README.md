# prometheus

Role prometheus fully automates deployment of Prometheus and all its configuration.

## Table of contents

- [Requirements](#requirements)
- [Default Variables](#default-variables)
  - [prometheus_actions](#prometheus_actions)
  - [prometheus_bin_dir](#prometheus_bin_dir)
  - [prometheus_config](#prometheus_config)
  - [prometheus_dir](#prometheus_dir)
  - [prometheus_download_base](#prometheus_download_base)
  - [prometheus_download_dir](#prometheus_download_dir)
  - [prometheus_retention_size](#prometheus_retention_size)
  - [prometheus_retention_time](#prometheus_retention_time)
  - [prometheus_state](#prometheus_state)
  - [prometheus_user](#prometheus_user)
  - [prometheus_version](#prometheus_version)
- [Dependencies](#dependencies)
- [License](#license)
- [Author](#author)

---

## Requirements

- Minimum Ansible version: `2.20`

## Default Variables

### prometheus_actions

List of actions the role does, accepts one or more actions.
Use comma without spaces as a delimiter for multiple actions.

**_Required:_** `true`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  prometheus_actions: install
  prometheus_actions: install,state_control
```

### prometheus_bin_dir

PATH directory for installed binaries

**_Type:_** String<br />

#### Default value

```YAML
prometheus_bin_dir: /usr/local/bin
```

### prometheus_config

Prometheus default configuration

**_Type:_** Dict<br />

#### Default value

```YAML
prometheus_config:
  global:
    scrape_interval: 15s
  scrape_configs:
    - job_name: targets
      static_configs:
        - targets:
            - localhost:9090
```

### prometheus_dir

Location of Prometheus data and configuration

**_Type:_** String<br />

#### Default value

```YAML
prometheus_dir: /opt/prometheus
```

### prometheus_download_base

Base URL to download installation artifacts

**_Type:_** String<br />

#### Default value

```YAML
prometheus_download_base: https://github.com/prometheus/prometheus/releases/download
```

### prometheus_download_dir

Destination directory for downloading Prometheus binaries

**_Type:_** String<br />

#### Default value

```YAML
prometheus_download_dir: /tmp
```

### prometheus_retention_size

Prometheus data retention size

**_Type:_** String<br />

#### Default value

```YAML
prometheus_retention_size: 10GB
```

### prometheus_retention_time

Prometheus data retention time

**_Type:_** String<br />

#### Default value

```YAML
prometheus_retention_time: 15d
```

### prometheus_state

Target state for the Prometheus daemon

**_Required:_** `true`, only in case `prometheus_actions: state_control`<br />
**_Type:_** String<br />

#### Example usage

```YAML
  prometheus_state: started
  prometheus_state: restarted
```

### prometheus_user

Linux user name to run the Prometheus service

**_Type:_** String<br />

#### Default value

```YAML
prometheus_user: prometheus
```

### prometheus_version

Prometheus version to be installed

**_Type:_** String<br />

#### Default value

```YAML
prometheus_version: 3.5.1
```

## Dependencies

None.

## License

MIT

## Author

freedform
