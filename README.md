<!-- This file was automatically generated by the `build-harness`. Make all changes to `README.yaml` and run `make readme` to rebuild this file. -->

[![Cloud Posse](https://cloudposse.com/logo-300x69.png)](https://cloudposse.com)

# terraform-aws-alb [![Build Status](https://travis-ci.org/cloudposse/terraform-aws-alb.svg?branch=master)](https://travis-ci.org/cloudposse/terraform-aws-alb) [![Latest Release](https://img.shields.io/github/release/cloudposse/terraform-aws-alb.svg)](https://github.com/cloudposse/terraform-aws-alb/releases) [![Slack Community](https://slack.cloudposse.com/badge.svg)](https://slack.cloudposse.com)


Terraform module to create an ALB, default ALB listener(s), and a default ALB target and related security groups.


---

This project is part of our comprehensive ["SweetOps"](https://docs.cloudposse.com) approach towards DevOps. 


It's 100% Open Source and licensed under the [APACHE2](LICENSE).




## Usage

Include this module in your existing terraform code:

```hcl
module "alb" {
  source             = "git::https://github.com/cloudposse/terraform-aws-alb.git?ref=tags/0.2.0"
  namespace          = "eg"
  name               = "app"
  stage              = "dev"

  vpc_id             = "xxxxxxxxx"
  ip_address_type    = "ipv4"

  subnet_ids         = ["xxxxxxxx", "xxxxxxxx"]
  access_logs_region = "us-west-2"
}
```






## Makefile Targets
```
Available targets:

  help                                This help screen
  help/all                            Display help for all targets
  lint                                Lint terraform code

```

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| access_logs_enabled | A boolean flag to enable/disable access_logs | string | `true` | no |
| access_logs_prefix | The S3 bucket prefix | string | `` | no |
| access_logs_region | The region for the access_logs S3 bucket | string | `us-east-1` | no |
| attributes | Additional attributes, e.g. `1` | list | `<list>` | no |
| certificate_arn | The ARN of the default SSL certificate for HTTPS listener | string | `` | no |
| cross_zone_load_balancing_enabled | A boolean flag to enable/disable cross zone load balancing | string | `true` | no |
| deletion_protection_enabled | A boolean flag to enable/disable deletion protection for ALB | string | `false` | no |
| delimiter | Delimiter to be used between `namespace`, `name`, `stage` and `attributes` | string | `-` | no |
| deregistration_delay | The amount of time to wait in seconds before changing the state of a deregistering target to unused | string | `15` | no |
| health_check_healthy_threshold | The number of consecutive health checks successes required before considering an unhealthy target healthy | string | `2` | no |
| health_check_interval | The duration in seconds in between health checks | string | `15` | no |
| health_check_matcher | The HTTP response codes to indicate a healthy check | string | `200-399` | no |
| health_check_path | The destination for the health check request | string | `/` | no |
| health_check_timeout | The amount of time to wait in seconds before failing a health check request | string | `10` | no |
| health_check_unhealthy_threshold | The number of consecutive health check failures required before considering the target unhealthy | string | `2` | no |
| http2_enabled | A boolean flag to enable/disable HTTP/2 | string | `true` | no |
| http_enabled | A boolean flag to enable/disable HTTP listener | string | `true` | no |
| http_ingress_cidr_blocks | List of CIDR blocks to allow in HTTP security group | list | `<list>` | no |
| http_ingress_prefix_list_ids | List of prefix list IDs for allowing access to HTTP ingress security group | list | `<list>` | no |
| http_port | The port for the HTTP listener | string | `80` | no |
| https_enabled | A boolean flag to enable/disable HTTPS listener | string | `false` | no |
| https_ingress_cidr_blocks | List of CIDR blocks to allow in HTTPS security group | list | `<list>` | no |
| https_ingress_prefix_list_ids | List of prefix list IDs for allowing access to HTTPS ingress security group | list | `<list>` | no |
| https_port | The port for the HTTPS listener | string | `443` | no |
| idle_timeout | The time in seconds that the connection is allowed to be idle | string | `60` | no |
| internal | A boolean flag to determine whether the ALB should be internal | string | `false` | no |
| ip_address_type | The type of IP addresses used by the subnets for your load balancer. The possible values are `ipv4` and `dualstack`. | string | `ipv4` | no |
| name | Solution name, e.g. `app` | string | - | yes |
| namespace | Namespace, which could be your organization name, e.g. `cp` or `cloudposse` | string | - | yes |
| security_group_ids | A list of additional security group IDs to allow access to ALB | list | `<list>` | no |
| stage | Stage, e.g. `prod`, `staging`, `dev`, or `test` | string | - | yes |
| subnet_ids | A list of subnet IDs to associate with ALB | list | - | yes |
| tags | Additional tags (e.g. `map(`BusinessUnit`,`XYZ`) | map | `<map>` | no |
| vpc_id | VPC ID to associate with ALB | string | - | yes |

## Outputs

| Name | Description |
|------|-------------|
| access_logs_bucket_id | The S3 bucket ID for access logs |
| alb_arn | The ARN of the ALB |
| alb_arn_suffix | The ARN suffix of the ALB |
| alb_dns_name | DNS name of ALB |
| alb_name | The ARN suffix of the ALB |
| alb_zone_id | The ID of the zone which ALB is provisioned |
| default_target_group_arn | The default target group ARN |
| http_listener_arn | The ARN of the HTTP listener |
| https_listener_arn | The ARN of the HTTPS listener |
| listener_arns | A list of all the listener ARNs |
| security_group_id | The security group ID of the ALB |




## Related Projects

Check out these related projects.

- [terraform-aws-alb-ingress](https://github.com/cloudposse/terraform-aws-alb-ingress) - Terraform module to provision an HTTP style ingress rule based on hostname and path for an ALB


## Help

**Got a question?**

File a GitHub [issue](https://github.com/cloudposse/terraform-aws-alb/issues), send us an [email][email] or join our [Slack Community][slack].

## Commerical Support

Work directly with our team of DevOps experts via email, slack, and video conferencing. 

We provide *commercial support* for all of our [Open Source][github] projects. As a *Dedicated Support* customer, you have access to our team of subject matter experts at a fraction of the cost of a fulltime engineer. 

[![E-Mail](https://img.shields.io/badge/email-hello@cloudposse.com-blue.svg)](mailto:hello@cloudposse.com)

- **Questions.** We'll use a Shared Slack channel between your team and ours.
- **Troubleshooting.** We'll help you triage why things aren't working.
- **Code Reviews.** We'll review your Pull Requests and provide constructive feedback.
- **Bug Fixes.** We'll rapidly work to fix any bugs in our projects.
- **Build New Terraform Modules.** We'll develop original modules to provision infrastructure.
- **Cloud Architecture.** We'll assist with your cloud strategy and design.
- **Implementation.** We'll provide hands on support to implement our reference architectures. 


## Community Forum

Get access to our [Open Source Community Forum][slack] on Slack. It's **FREE** to join for everyone! Our "SweetOps" community is where you get to talk with others who share a similar vision for how to rollout and manage infrastructure. This is the best place to talk shop, ask questions, solicit feedback, and work together as a community to build *sweet* infrastructure.

## Contributing

### Bug Reports & Feature Requests

Please use the [issue tracker](https://github.com/cloudposse/terraform-aws-alb/issues) to report any bugs or file feature requests.

### Developing

If you are interested in being a contributor and want to get involved in developing this project or [help out](https://github.com/orgs/cloudposse/projects/3) with our other projects, we would love to hear from you! Shoot us an [email](mailto:hello@cloudposse.com).

In general, PRs are welcome. We follow the typical "fork-and-pull" Git workflow.

 1. **Fork** the repo on GitHub
 2. **Clone** the project to your own machine
 3. **Commit** changes to your own branch
 4. **Push** your work back up to your fork
 5. Submit a **Pull Request** so that we can review your changes

**NOTE:** Be sure to merge the latest changes from "upstream" before making a pull request!

## Copyright

Copyright © 2017-2018 [Cloud Posse, LLC](https://cloudposse.com)


## License 

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0) 

See [LICENSE](LICENSE) for full details.

    Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

      https://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.


## Trademarks

All other trademarks referenced herein are the property of their respective owners.

## About

This project is maintained and funded by [Cloud Posse, LLC][website]. Like it? Please let us know at <hello@cloudposse.com>

[![Cloud Posse](https://cloudposse.com/logo-300x69.png)](https://cloudposse.com)

We're a [DevOps Professional Services][hire] company based in Los Angeles, CA. We love [Open Source Software](https://github.com/cloudposse/)!

We offer paid support on all of our projects.  

Check out [our other projects][github], [apply for a job][jobs], or [hire us][hire] to help with your cloud strategy and implementation.

  [docs]: https://docs.cloudposse.com/
  [website]: https://cloudposse.com/
  [github]: https://github.com/cloudposse/
  [jobs]: https://cloudposse.com/jobs/
  [hire]: https://cloudposse.com/contact/
  [slack]: https://slack.cloudposse.com/
  [linkedin]: https://www.linkedin.com/company/cloudposse
  [twitter]: https://twitter.com/cloudposse/
  [email]: mailto:hello@cloudposse.com


### Contributors

|  [![Erik Osterman][osterman_avatar]](osterman_homepage)<br/>[Erik Osterman][osterman_homepage] | [![Igor Rodionov][goruha_avatar]](goruha_homepage)<br/>[Igor Rodionov][goruha_homepage] | [![Andriy Knysh][aknysh_avatar]](aknysh_homepage)<br/>[Andriy Knysh][aknysh_homepage] | [![Sarkis Varozian][sarkis_avatar]](sarkis_homepage)<br/>[Sarkis Varozian][sarkis_homepage] |
|---|---|---|---|

  [osterman_homepage]: https://github.com/osterman
  [osterman_avatar]: https://github.com/osterman.png?size=150
  [goruha_homepage]: https://github.com/goruha
  [goruha_avatar]: https://github.com/goruha.png?size=150
  [aknysh_homepage]: https://github.com/aknysh
  [aknysh_avatar]: https://github.com/aknysh.png?size=150
  [sarkis_homepage]: https://github.com/sarkis
  [sarkis_avatar]: https://github.com/sarkis.png?size=150


