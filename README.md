**Terraform**
An Open-Source, cloud-agnostic Infrastructure-as-code (IAC)

Terraform Workflow
Init → Plan → Apply → Destroy
 
Terraform Language
Declarative language, specify infrastructure objects, with .tf and .tf.json file extensions.  
Each terraform configuration has its root module, which has .tf files, a collection of such files together in a directory is considered as a module. A terraform module may have subdirectories with Terraform configuration files but only the top-level configuration files in a directory are part of that module. The sub-directories are treated as separate modules.
Terraform language consists of only a few basic elements called building blocks
<block_type> “<block_label>” “<block_label>”{
# block_body
<identifier> = <expression> # argument
}

Terraform Registry
Terraform registry is like a hub to get all the reusable components for providers and modules. The URL to terraform registry is https://registry.terraform.io/ 

Terraform Providers
Terraform should declare the providers to be able to download the respective files needed. 
versions.tf (settings.tf)-> Typically used to define the required Terraform version and provider versions, helps in ensuring that the correct versions of Terraform and providers are used, preventing compatibility issues.

#versions.tf
terraform{
    required_version = ">= 1.3.0"
    required_providers{
        azurerm{
            source = "hashicorp/azurerm"
            version = "~> 3.0"
        }
    }
}

~> is called pessimistic constraint operator
version = "~> 3.0" → Allows any version ≥ 3.0.0 but < 4.0.0
version = "~> 3.1" → Allows any version ≥ 3.1.0 but < 3.2.0
Source should be of the form [<HOSTNAME>/]<NAMESPACE>/<TYPE>
HOSTNAME part can be ignored if Terraform registry is used
e.g. “hashicorp/aws” instead of “terraform.registry.io/hashicorp/aws”

providers.tf (configuration.tf) -> Defines provider configurations like authentication, subscription details, or region settings, typically contains credentials, endpoints, or other provider-specific settings
#providers.tf  
provider "aws" {
    region = <AWS_REGION>
    access_key = <ACCESS_KEY>
    secret_key = <SECRET_KEY>
}
