Table of Contents
=================

   * [About this project](#about-this-project)
   * [Pre-requisites](#pre-requisites)
      * [Setup address-index-api](#setup-address-index-api)
      * [Setup Gatling](#setup-gatling)
      * [OS Tuning](#os-tuning)
   * [Usage](#usage)
   * [Configuration](#configuration)

# About this project
This project is a repository of Gatling based performance tests targeted at individual endpoints in address-index-api.

# Pre-requisites

## Setup address-index-api, address-index-demo-ui, address-index-data
TBD

## Setup Gatling
As a part of setting up address-index-api [above](#address-index-api), you will have all the pre-requisites in place to run the gatling scenarios in this project.

Setup involves:

1. Downloading the zip bundle from [gatling.io](https://gatling.io/download/) and,
2. Setting the `GATLING_HOME` environment variable depending on where the above bundle has been unzipped.

## OS Tuning
In order to subject any kind of meaningful load, OS tuning must be done in order to raise or un-restrict resource consumption limits imposed by consumer oriented OSes.

On macOS, the constraints most relevant to Gatling load tests include:

1. The maximum number of open files (`sysctl kern.maxfiles` )
2. The maximum number of open files per process (`sysctl kern.maxfilesperproc` )
3. The maximum number of open processes
4. The maximum number of open ports ('ephemeral port limit')
5. The maximum time before a TCP socket can be re-used

Instructions on altering all of the above limits is detailed in [macOS Tuning for Gatling](macOS%20Tuning%20for%20Gatling.md)


# Usage

The gatling scenarios are executed using the official gatling SBT plugin. Sample usages:

To simply run the scenario(s):
`sbt gatling:test`


To pass in a configurable property to the scenario(s):
`JAVA_OPTS="-DconcurrentUsers=10000" sbt gatling:test`


# Configuration

The list of configurable properties is visible in the `.conf` files in test/resources

# License

Copyright © 2017, Office for National Statistics (https://www.ons.gov.uk)

Released under MIT license, see [LICENSE](LICENSE.md) for details.
