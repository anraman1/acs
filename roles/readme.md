## The following Ansible task validates the ACS Operator installation and creates an init-bundle

# extra_vars 
  
  - by default, it will create a init-bundle as init_bundle_{ocp_cluster_name}
  - if you want custom name, please pass extra_vars: \
     **'init_bundle_name': < bundle_name >** \
      this name will be siffix to init_bundle_{ocp_cluster_name}_{init_bundle_name}
  - same format will be used when creating init-bundle-credential in AAP \
    ecs_init_bundle_{ocp_cluster_name}_{init_bundle_name} when passing extra_vars \
    else \
    ecs_init_bundle_{ocp_cluster_name} 
  
  ## ansible credential type

  Name: ecs_init_bundle

  #Input configuration
  ```
  fields:
  - id: init_bundle
    type: string
    label: ACS Init-Bundle
    secret: true
    multiline: true
required:
  - init_bundle

```
## Injector configuration

```
env:
  ACS_INIT_BUNDLE: '{{ init_bundle }}'
extra_vars:
  init_bundle: '{{ init_bundle }}'

```
