# Project Site Model

A project "site model" contains information necessary to specify the configuration for
a particular site. This is a logical representation of the underlying information, and can be
applied against different cloud projects or device configurations to ensure that things are
configured appropriately. It's fundamentally the building model that describes the on-prem
devices and how they communicate with the cloud.

An site model directory shows specific examples of how this would be constructed for a complete
site. Typically, however, each site would have its own git repo (with the `cloud_iot_config.json`
file in the repo root). For test and development, this only needs to be a on-disk directory.

At a high-level, the various constructs relevant to UDMI are (described in more detail below):
* `cloud_iot_config.json`
* `devices`

## `cloud_iot_config.json`

```
{
  "cloud_region": "us-central1",
  "site_name": "ZZ-TRI-FECTA",
  "registry_id": "registrar_test"
}
```

* `cloud_region`: The cloud region associated with this site. This is used by various tools as
required for API calls.
* `site_name`: The semantic name of the site, which is used for various bits of validation and
reporting.
* `registry_id`: The Cloud IoT Core _registry_ id for this site.

## `devices/`

The `devices` directory contains a set of descriptions for individual devices in the system. Each
device directory name corresponds to the Cloud IoT Core device entry and represents the canonical
name for the device. Inside of this directory will be various bits and pieces of information used
by different tools for managing the devices.

* `generated_config.json`: Generated default config block (generated by the `registrar` tool).
* `metadata.json`: Metadata description of the device.
* `metadata_norm.json`: Generated normalized version of the `metadata.json` file.
* `rsa_private.pem`: Private device key.
* `rsa_private.pkcs8`: Private device key (binary format).
* `rsa_public.pem`: Public device key (for registering with the cloud registry).
