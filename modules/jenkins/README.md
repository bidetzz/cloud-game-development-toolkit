# [Jenkins](https://www.jenkins.io/)

Jenkins is an open source automation server. It helps automate the parts of software development related to building, testing, and deploying, facilitating continuous integration, and continuous delivery.

This module deploys the following resources:

- An Elastic Container Service (ECS) cluster backed by AWS Fargate.
- An ECS service running the latest Jenkins container ([jenkins/jenkins:lts-jdk17](https://hub.docker.com/r/jenkins/jenkins)) available.
- An Elastic File System (EFS) for the Jenkins service to use as a persistent datastore.
- An Elastic Load Balancer (ELB) for TLS termination of the Jenkins service
- A configurable number of EC2 Autoscaling groups to serve as a flexible pool of build nodes for the Jenkins service
- Supporting resources including KMS keys for encryption and IAM roles to ensure security best practices

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 5.30 |
| <a name="requirement_random"></a> [random](#requirement\_random) | >=3.6 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | >= 5.30 |
| <a name="provider_random"></a> [random](#provider\_random) | >=3.6 |

## Modules

No modules.

## Resources

| Name | Type |
|------|------|
| [aws_autoscaling_group.jenkins_build_farm_asg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/autoscaling_group) | resource |
| [aws_cloudwatch_log_group.jenkins_service_log_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/cloudwatch_log_group) | resource |
| [aws_ecs_cluster.jenkins_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ecs_cluster) | resource |
| [aws_ecs_cluster_capacity_providers.jenkins_cluster_fargate_rpvodiers](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ecs_cluster_capacity_providers) | resource |
| [aws_ecs_service.jenkins_service](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ecs_service) | resource |
| [aws_ecs_task_definition.jenkins_task_definition](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/ecs_task_definition) | resource |
| [aws_efs_access_point.jenkins_efs_access_point](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_access_point) | resource |
| [aws_efs_file_system.jenkins_efs_file_system](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_file_system) | resource |
| [aws_efs_mount_target.jenkins_efs_mount_target](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/efs_mount_target) | resource |
| [aws_fsx_openzfs_file_system.jenkins_build_farm_fsxz_file_system](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/fsx_openzfs_file_system) | resource |
| [aws_iam_instance_profile.build_farm_instance_profile](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_instance_profile) | resource |
| [aws_iam_policy.build_farm_fsxz_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.build_farm_s3_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.ec2_fleet_plugin_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_policy.jenkins_default_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_iam_role.build_farm_role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role.jenkins_default_role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role.jenkins_task_execution_role](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role) | resource |
| [aws_iam_role_policy_attachment.ec2_fleet_plugin_policy_attachment](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_role_policy_attachment) | resource |
| [aws_launch_template.jenkins_build_farm_launch_template](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/launch_template) | resource |
| [aws_lb.jenkins_alb](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb) | resource |
| [aws_lb_listener.jenkins_alb_https_listener](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb_listener) | resource |
| [aws_lb_target_group.jenkins_alb_target_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lb_target_group) | resource |
| [aws_s3_bucket.artifact_buckets](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket) | resource |
| [aws_s3_bucket.jenkins_alb_access_logs_bucket](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/s3_bucket) | resource |
| [aws_security_group.jenkins_alb_sg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group.jenkins_build_farm_sg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group.jenkins_build_storage_sg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group.jenkins_efs_security_group](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_security_group.jenkins_service_sg](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/security_group) | resource |
| [aws_vpc_security_group_egress_rule.jenkins_alb_outbound_service](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_egress_rule) | resource |
| [aws_vpc_security_group_egress_rule.jenkins_service_outbound_ipv4](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_egress_rule) | resource |
| [aws_vpc_security_group_egress_rule.jenkins_service_outbound_ipv6](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_egress_rule) | resource |
| [aws_vpc_security_group_ingress_rule.jenkins_build_farm_inbound_ssh_service](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_ingress_rule) | resource |
| [aws_vpc_security_group_ingress_rule.jenkins_build_vpc_all_traffic](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_ingress_rule) | resource |
| [aws_vpc_security_group_ingress_rule.jenkins_efs_inbound_service](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_ingress_rule) | resource |
| [aws_vpc_security_group_ingress_rule.jenkins_service_inbound_alb](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/vpc_security_group_ingress_rule) | resource |
| [random_string.artifact_buckets](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [random_string.build_farm](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [random_string.fsxz](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [random_string.jenkins](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [random_string.jenkins_alb_access_logs_bucket_suffix](https://registry.terraform.io/providers/hashicorp/random/latest/docs/resources/string) | resource |
| [aws_caller_identity.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/caller_identity) | data source |
| [aws_ecs_cluster.jenkins_cluster](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/ecs_cluster) | data source |
| [aws_iam_policy_document.build_farm_fsxz_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.build_farm_s3_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.ec2_fleet_plugin_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.ec2_trust_relationship](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.ecs_tasks_trust_relationship](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_iam_policy_document.jenkins_default_policy](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |
| [aws_region.current](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/region) | data source |
| [aws_vpc.build_farm_vpc](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/vpc) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_artifact_buckets"></a> [artifact\_buckets](#input\_artifact\_buckets) | List of Amazon S3 buckets you wish to create to store build farm artifacts. | <pre>map(<br>    object({<br>      name                 = string<br>      enable_force_destroy = optional(bool, true)<br>  }))</pre> | `null` | no |
| <a name="input_build_farm_compute"></a> [build\_farm\_compute](#input\_build\_farm\_compute) | Each object in this map corresponds to an ASG used by Jenkins as build agents. | <pre>map(object(<br>    {<br>      ami = string<br>      #TODO: Support mixed instances / spot with custom policies<br>      instance_type     = string<br>      ebs_optimized     = optional(bool, true)<br>      enable_monitoring = optional(bool, true)<br>    }<br>  ))</pre> | `{}` | no |
| <a name="input_build_farm_fsx_openzfs_storage"></a> [build\_farm\_fsx\_openzfs\_storage](#input\_build\_farm\_fsx\_openzfs\_storage) | Each object in this map corresponds to an FSx OpenZFS file system used by the Jenkins build agents. | <pre>map(object(<br>    {<br>      storage_capacity    = number<br>      throughput_capacity = number<br>      storage_type        = optional(string, "SSD") # "SSD", "HDD"<br>      deployment_type     = optional(string, "SINGLE_AZ_1")<br>      route_table_ids     = optional(list(string), null)<br>    }<br>  ))</pre> | `{}` | no |
| <a name="input_build_farm_subnets"></a> [build\_farm\_subnets](#input\_build\_farm\_subnets) | The subnets to deploy the build farms into. | `list(string)` | n/a | yes |
| <a name="input_certificate_arn"></a> [certificate\_arn](#input\_certificate\_arn) | The TLS certificate ARN for the Jenkins service load balancer. | `string` | n/a | yes |
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name) | The ARN of the cluster to deploy the Jenkins service into. Defaults to null and a cluster will be created. | `string` | `null` | no |
| <a name="input_container_cpu"></a> [container\_cpu](#input\_container\_cpu) | The CPU allotment for the Jenkins container. | `number` | `1024` | no |
| <a name="input_container_memory"></a> [container\_memory](#input\_container\_memory) | The memory allotment for the Jenkins container. | `number` | `4096` | no |
| <a name="input_container_name"></a> [container\_name](#input\_container\_name) | The name of the Jenkins service container. | `string` | `"jenkins-container"` | no |
| <a name="input_container_port"></a> [container\_port](#input\_container\_port) | The container port used by the Jenkins service container. | `number` | `8080` | no |
| <a name="input_create_ec2_fleet_plugin_policy"></a> [create\_ec2\_fleet\_plugin\_policy](#input\_create\_ec2\_fleet\_plugin\_policy) | Optional creation of IAM Policy required for Jenkins EC2 Fleet plugin. Default is set to false. | `bool` | `false` | no |
| <a name="input_create_jenkins_default_policy"></a> [create\_jenkins\_default\_policy](#input\_create\_jenkins\_default\_policy) | Optional creation of Jenkins Default IAM Policy. Default is set to true. | `bool` | `true` | no |
| <a name="input_create_jenkins_default_role"></a> [create\_jenkins\_default\_role](#input\_create\_jenkins\_default\_role) | Optional creation of Jenkins Default IAM Role. Default is set to true. | `bool` | `true` | no |
| <a name="input_custom_jenkins_role"></a> [custom\_jenkins\_role](#input\_custom\_jenkins\_role) | ARN of the custom IAM Role you wish to use with Jenkins. | `string` | `null` | no |
| <a name="input_enable_jenkins_alb_access_logs"></a> [enable\_jenkins\_alb\_access\_logs](#input\_enable\_jenkins\_alb\_access\_logs) | Enables access logging for the Jenkins ALB. Defaults to false. | `bool` | `false` | no |
| <a name="input_enable_jenkins_alb_deletion_protection"></a> [enable\_jenkins\_alb\_deletion\_protection](#input\_enable\_jenkins\_alb\_deletion\_protection) | Enables deletion protection for the Jenkins ALB. Defaults to false. | `bool` | `false` | no |
| <a name="input_environment"></a> [environment](#input\_environment) | The current environment (e.g. dev, prod, etc.) | `string` | `"dev"` | no |
| <a name="input_existing_artifact_buckets"></a> [existing\_artifact\_buckets](#input\_existing\_artifact\_buckets) | List of ARNs of the S3 buckets used to store artifacts created by the build farm. | `list(string)` | `[]` | no |
| <a name="input_existing_security_groups"></a> [existing\_security\_groups](#input\_existing\_security\_groups) | A list of existing security group IDs to attach to the Jenkins service load balancer. | `list(string)` | `null` | no |
| <a name="input_internal"></a> [internal](#input\_internal) | Set this flag to true if you do not want the Jenkins service load balancer to have a public IP. | `bool` | `false` | no |
| <a name="input_jenkins_agent_secret_arns"></a> [jenkins\_agent\_secret\_arns](#input\_jenkins\_agent\_secret\_arns) | A list of secretmanager ARNs (wildcards allowed) that contain any secrets which need to be accessed by the Jenkins service. | `list(string)` | `null` | no |
| <a name="input_jenkins_alb_access_logs_bucket"></a> [jenkins\_alb\_access\_logs\_bucket](#input\_jenkins\_alb\_access\_logs\_bucket) | ID of the S3 bucket for Jenkins ALB access log storage. If access logging is enabled and this is null the module creates a bucket. | `string` | `null` | no |
| <a name="input_jenkins_alb_access_logs_prefix"></a> [jenkins\_alb\_access\_logs\_prefix](#input\_jenkins\_alb\_access\_logs\_prefix) | Log prefix for Jenkins ALB access logs. If null the project prefix and module name are used. | `string` | `null` | no |
| <a name="input_jenkins_alb_subnets"></a> [jenkins\_alb\_subnets](#input\_jenkins\_alb\_subnets) | A list of subnets to deploy the Jenkins load balancer into. Public subnets are recommended. | `list(string)` | n/a | yes |
| <a name="input_jenkins_cloudwatch_log_retention_in_days"></a> [jenkins\_cloudwatch\_log\_retention\_in\_days](#input\_jenkins\_cloudwatch\_log\_retention\_in\_days) | The log retention in days of the cloudwatch log group for Jenkins. | `string` | `365` | no |
| <a name="input_jenkins_efs_performance_mode"></a> [jenkins\_efs\_performance\_mode](#input\_jenkins\_efs\_performance\_mode) | The performance mode of the EFS file system used by the Jenkins service. Defaults to general purpose. | `string` | `"generalPurpose"` | no |
| <a name="input_jenkins_efs_throughput_mode"></a> [jenkins\_efs\_throughput\_mode](#input\_jenkins\_efs\_throughput\_mode) | The throughput mode of the EFS file system used by the Jenkins service. Defaults to bursting. | `string` | `"bursting"` | no |
| <a name="input_jenkins_service_desired_container_count"></a> [jenkins\_service\_desired\_container\_count](#input\_jenkins\_service\_desired\_container\_count) | The desired number of containers running the Jenkins service. | `number` | `1` | no |
| <a name="input_jenkins_service_subnets"></a> [jenkins\_service\_subnets](#input\_jenkins\_service\_subnets) | A list of subnets to deploy the Jenkins service into. Private subnets are recommended. | `list(string)` | n/a | yes |
| <a name="input_name"></a> [name](#input\_name) | The name attached to Jenkins module resources. | `string` | `"jenkins"` | no |
| <a name="input_project_prefix"></a> [project\_prefix](#input\_project\_prefix) | The project prefix for this workload. This is appeneded to the beginning of most resource names. | `string` | `"cgd"` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | Tags to apply to resources. | `map(any)` | <pre>{<br>  "IAC_MANAGEMENT": "CGD-Toolkit",<br>  "IAC_MODULE": "Jenkins",<br>  "IAC_PROVIDER": "Terraform"<br>}</pre> | no |
| <a name="input_vpc_id"></a> [vpc\_id](#input\_vpc\_id) | The ID of the existing VPC you would like to deploy the Jenkins service and build farms into. | `string` | n/a | yes |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_alb_security_group"></a> [alb\_security\_group](#output\_alb\_security\_group) | Security group associated with the Jenkins load balancer |
| <a name="output_build_farm_security_group"></a> [build\_farm\_security\_group](#output\_build\_farm\_security\_group) | Security group associated with the build farm autoscaling groups |
| <a name="output_service_security_group"></a> [service\_security\_group](#output\_service\_security\_group) | Security group associated with the ECS service hosting jenkins |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->