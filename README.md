# terraform-workspaces
1 -  terraform workspace new tst
 
Created and switched to workspace "dev"!
 
You're now on a new, empty workspace. Workspaces isolate their state,
so if you run "terraform plan" Terraform will not see any existing state
for this configuration.



2 -  terraform plan -out=tftst_plan -var 'env=tst'
 
Terraform used the selected providers to generate the following execution plan. Resource actions are indicated with the
following symbols:
  + create
 
Terraform will perform the following actions:
 
  # aws_s3_bucket.tf_code will be created
  + resource "aws_s3_bucket" "tf_code" {
      + acceleration_status         = (known after apply)
      + acl                         = "private"
      + arn                         = (known after apply)
      + bucket                      = (known after apply)
      + bucket_domain_name          = (known after apply)
      + bucket_regional_domain_name = (known after apply)
      + force_destroy               = true
      + hosted_zone_id              = (known after apply)
      + id                          = (known after apply)
      + region                      = (known after apply)
      + request_payer               = (known after apply)
      + tags                        = {
          + "Name" = "tf_bucket"
        }
      + tags_all                    = {
          + "Name" = "tf_bucket"
        }
      + website_domain              = (known after apply)
      + website_endpoint            = (known after apply)
 
      + versioning {
          + enabled    = (known after apply)
          + mfa_delete = (known after apply)
        }
    }
 
  # random_id.tf_bucket_id will be created
  + resource "random_id" "tf_bucket_id" {
      + b64_std     = (known after apply)
      + b64_url     = (known after apply)
      + byte_length = 2
      + dec         = (known after apply)
      + hex         = (known after apply)
      + id          = (known after apply)
    }
 
Plan: 2 to add, 0 to change, 0 to destroy.
 
Changes to Outputs:
  + bucketname = (known after apply)
 
───────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
 
Saved the plan to: tfdev_plan
 
To perform exactly these actions, run the following command to apply:
    terraform apply "tfdev_plan"
 
3 - terraform apply "tftst_plan"
 
random_id.tf_bucket_id: Creating...
random_id.tf_bucket_id: Creation complete after 0s [id=3SM]
aws_s3_bucket.tf_code: Creating...
aws_s3_bucket.tf_code: Creation complete after 5s [id=ga-terraform-dev-56611]
 
Apply complete! Resources: 2 added, 0 changed, 0 destroyed.
 
Outputs:
 
bucketname = "ga-terraform-dev-56611"
 
