# 30 Most Asked Terraform Interview Questions

## 1. What is Terraform?

Terraform is an Infrastructure as Code (IaC) tool that allows you to
define and provision infrastructure using declarative configuration
files.

## 2. What is Infrastructure as Code (IaC)?

IaC is the practice of managing and provisioning infrastructure through
code instead of manual processes.

## 3. What are Terraform providers?

Providers are plugins that allow Terraform to interact with cloud
platforms, SaaS providers, and other APIs (e.g., AWS, Azure, GCP).

## 4. What is a Terraform state file?

The state file stores the current state of managed infrastructure and
maps real-world resources to configuration.

## 5. What is the difference between terraform plan and terraform apply?

-   plan: Shows execution plan.
-   apply: Executes changes required to reach desired state.

## 6. What is terraform init?

Initializes a working directory by downloading providers and setting up
backend.

## 7. What are Terraform modules?

Reusable, self-contained Terraform configurations.

## 8. What is a backend in Terraform?

Defines where the state file is stored (local or remote).

## 9. What is remote state?

State stored remotely (e.g., S3, Terraform Cloud) for collaboration.

## 10. What is terraform refresh?

Updates state file with real-world infrastructure.

## 11. What is terraform destroy?

Removes all managed infrastructure resources.

## 12. What are input variables?

Variables used to parameterize Terraform configurations.

## 13. What are output variables?

Values exported from a module after apply.

## 14. What is a data source?

Used to fetch information from existing infrastructure.

## 15. What is the difference between count and for_each?

Both create multiple resources; for_each works better with maps and
sets.

## 16. What is Terraform Cloud?

A managed service for running Terraform in the cloud.

## 17. What is Terraform workspace?

Used to manage multiple state files for different environments.

## 18. What is dependency in Terraform?

Resource creation order defined automatically or using depends_on.

## 19. What is a provisioner?

Executes scripts on local or remote machines during resource creation.

## 20. What is the lifecycle block?

Controls resource behavior (create_before_destroy, prevent_destroy).

## 21. What is terraform taint?

Marks a resource for recreation.

## 22. What is terraform import?

Imports existing infrastructure into Terraform state.

## 23. What is state locking?

Prevents concurrent state modifications.

## 24. What are dynamic blocks?

Used to dynamically construct nested configuration blocks.

## 25. What is the difference between mutable and immutable infrastructure?

Mutable modifies existing resources; immutable replaces them.

## 26. What is drift detection?

Detects differences between actual infrastructure and Terraform state.

## 27. What are locals in Terraform?

Local values assigned within configuration for reuse.

## 28. What is the difference between terraform validate and terraform fmt?

-   validate: Checks configuration validity.
-   fmt: Formats configuration files.

## 29. What are Terraform provisioner types?

Local-exec and remote-exec.

## 30. What are best practices for Terraform?

-   Use remote state
-   Use modules
-   Use version control
-   Avoid hardcoding secrets
-   Use workspaces for environments
