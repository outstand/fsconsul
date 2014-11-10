# fsconsul

fsconsul writes data to the filesystem by reading it from [Consul's K/V store](http://www.consul.io).

fsconsul allows configuration data to be placed on disk without a consuming application
needing to know about the existence of Consul. This makes it especially easy to configure
applications throughout all your environments: development, testing, production, etc.  On
any change, fsconsul will run the provided command, so you can perform any additional actions
(restarting your application, for example) necessary.

fsconsul is a port of [envconsul](https://github.com/hashicorp/envconsul) which in turn was inspired by [envdir](http://cr.yp.to/daemontools/envdir.html)
in its simplicity, name, and function.

## Download & Usage

To install fsconsul, clone this repo into your go workspace and do a `go install`.

Run `fsconsul` to see the usage help:

```

$ fsconsul
Usage: fsconsul [options] prefixes paths onchange...

  Write files to the specified locations on the local system by reading K/V
  from Consul's K/V store with the given prefixes and execute a program on
  any change.  Prefixes and paths must be pipe-delimited.

Options:

  -configFile="": json file containing all configuration (if this is provided, all other config is ignored)
  -addr="127.0.0.1:8500": consul HTTP API address with port
  -dc="": consul datacenter, uses local if blank
  -keystore="": directory of keys used for decryption
  -token="": token to use for ACL access
```

## CI

Builds are automatically run by Travis on any push or pull request.

![Travis Status](https://travis-ci.org/ryanbreen/fsconsul.svg?branch=master)