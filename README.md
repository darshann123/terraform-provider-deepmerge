# 🌊 Terraform Provider Deepmerge

![GitHub Release](https://img.shields.io/github/release/darshann123/terraform-provider-deepmerge.svg)

Welcome to the **Terraform Provider Deepmerge** repository! This project offers deepmerge functions for Terraform 1.8+ and OpenTofu. With this provider, you can efficiently manage and merge complex configurations in your Terraform projects.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)
- [Releases](#releases)

## Introduction

The **Terraform Provider Deepmerge** enables users to merge nested structures seamlessly. It simplifies configuration management by allowing you to combine multiple configuration files into a single, cohesive unit. This is particularly useful when working with multiple environments or modules in Terraform.

## Features

- **Deep Merge Support**: Efficiently merge complex, nested configurations.
- **Terraform 1.8+ Compatibility**: Designed to work with the latest Terraform versions.
- **OpenTofu Compatibility**: Provides support for OpenTofu deepmerge functions.
- **Easy Integration**: Simple to integrate into your existing Terraform workflows.

## Installation

To install the Terraform Provider Deepmerge, follow these steps:

1. **Download the latest release** from the [Releases page](https://github.com/darshann123/terraform-provider-deepmerge/releases).
2. **Unzip the downloaded file** and move the provider binary to your Terraform plugins directory.

For example, on a Unix-like system, you can run:

```bash
unzip terraform-provider-deepmerge_*.zip
mv terraform-provider-deepmerge ~/.terraform.d/plugins/
```

3. **Initialize your Terraform configuration** to load the new provider:

```bash
terraform init
```

## Usage

To use the Deepmerge provider in your Terraform configuration, add the following block to your `.tf` file:

```hcl
terraform {
  required_providers {
    deepmerge = {
      source  = "darshann123/deepmerge"
      version = ">= 1.0.0"
    }
  }
}

provider "deepmerge" {}
```

### Merging Configurations

You can use the `deepmerge` function in your Terraform resources. Here’s a basic example:

```hcl
locals {
  config_a = {
    key1 = "value1"
    nested = {
      key2 = "value2"
    }
  }

  config_b = {
    key1 = "value3"
    nested = {
      key3 = "value4"
    }
  }

  merged_config = deepmerge(local.config_a, local.config_b)
}

output "merged" {
  value = local.merged_config
}
```

This example demonstrates how to merge two configurations, resulting in a single output that contains all keys and values.

## Examples

Here are a few more examples to illustrate the power of the Deepmerge provider:

### Example 1: Merging Lists

```hcl
locals {
  list_a = ["item1", "item2"]
  list_b = ["item3", "item4"]

  merged_list = deepmerge(local.list_a, local.list_b)
}

output "merged_list" {
  value = local.merged_list
}
```

### Example 2: Complex Nested Structures

```hcl
locals {
  config_a = {
    database = {
      host = "localhost"
      port = 5432
    }
  }

  config_b = {
    database = {
      username = "user"
      password = "pass"
    }
  }

  merged_config = deepmerge(local.config_a, local.config_b)
}

output "database_config" {
  value = local.merged_config.database
}
```

## Contributing

We welcome contributions to the Terraform Provider Deepmerge project! If you would like to contribute, please follow these steps:

1. **Fork the repository**.
2. **Create a new branch** for your feature or bug fix.
3. **Make your changes** and commit them with clear messages.
4. **Push your changes** to your forked repository.
5. **Submit a pull request** for review.

Please ensure that your code adheres to the existing style and includes tests where applicable.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Releases

To check for the latest releases, visit the [Releases page](https://github.com/darshann123/terraform-provider-deepmerge/releases). Here, you can find the latest binaries and updates.

![GitHub Release](https://img.shields.io/github/release/darshann123/terraform-provider-deepmerge.svg)

Thank you for your interest in the Terraform Provider Deepmerge! We hope this tool enhances your Terraform experience and simplifies your configuration management.