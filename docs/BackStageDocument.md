# Backstage
Out of the box, Backstage includes:

1. Backstage Software Catalog for managing all your software (microservices, libraries, data pipelines, websites, ML models, etc.)

2. Backstage Software Templates for quickly spinning up new projects and standardizing your tooling with your organization’s best practices

3. Backstage TechDocs for making it easy to create, maintain, find, and use technical documentation, using a "docs like code" approach

## Backstage Software Catalog
The Backstage Software Catalog is a centralized system that keeps track of ownership and metadata for all the software in your ecosystem (services, websites, libraries, data pipelines, etc).


More specifically, the Software Catalog enables two main use-cases:

1. Helping teams manage and maintain the software they own. Teams get a uniform view of all their software; services, libraries, websites, ML models — you name it, Backstage knows all about it.
2. Makes all the software in your company, and who owns it, discoverable. No more orphan software hiding in the dark corners of your software ecosystem.

### Adding components to the catalog
There are 3 ways to add components to the catalog (refer link for more detail https://backstage.io/docs/features/software-catalog/software-catalog-overview):

1. Manually register components (Register component when you have your component) https://backstage.io/docs/features/software-catalog/software-catalog-overview
    - Step 1: Existing a component (project/service/libary and etc) on Github
    - Step 2: Create a yaml file and fill all information of your component in the file with format of Backstage (refer this link for more detail https://backstage.io/docs/features/software-catalog/descriptor-format). After then push it into your repository on Github
    - Step 3: Click button **REGISTER EXISTING COMPONENT** ![alt text for screen readers](images/register_existing_component.png)
    - Step 4: Copy the URL link of YAML file that you created at Step 2 and then paste the link to **Repository URL** input ![alt text for screen readers](images/register_existing_component_input_url.png)
    - Step 5: Backstage will validate after Click ANALYZE button 
    - Step 6: If the validation is success, IMPORT button will be displayed as below:  ![alt text for screen readers](images/register_existing_component_import.png)
    - Step 7: Finally, click **INPORT** button 

2. Creating new components through Backstage (Creating new component on Backstage) https://backstage.io/docs/features/software-templates/software-templates-index
    - Step 1: Click the Create button on left taskbar ![alt text for screen readers](images/new_component.png)
    - Step 2: Select a template that corresponds to your project ![alt text for screen readers](images/new_component_select_template.png)
    - Step 3: Fill information your component ![alt text for screen readers](images/new_component_information.png)
    - Step 4: Finally, backstage will generate the template and create a repository on your GitHub

3. Integrating with an external source: For existing system and you want intergate them with Backstage for keeping track. https://backstage.io/docs/features/software-catalog/external-integrations

### Descriptor Format of Catalog Entities
The descriptor format supports substitutions using $text, $json, and $yaml.
### Common to All Kinds: The Envelope
To understand the parameter below, please refer this link https://backstage.io/docs/features/software-catalog/descriptor-format
- apiVersion and kind [required]
 + kind:
- metadata [required]
    + name [required]
    + namespace [optional]
    + title [optional]
    + description [optional]
    + labels [optional]
    + annotations [optional]
    + tags [optional]
    + links [optional]
- spec [varies] 

![alt text for screen readers](images/software_catalog_backstage.png)

The following is an example of a descriptor file for a Component entity:
```yaml
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: artist-web
  description: The place to be, for great artists
  labels:
    example.com/custom: custom_label_value
  annotations:
    example.com/service-discovery: artistweb
    circleci.com/project-slug: github/example-org/artist-website
  tags:
    - java
  links:
    - url: https://admin.example-org.com
      title: Admin Dashboard
      icon: dashboard
spec:
  type: website
  lifecycle: production
  owner: artist-relations-team
  system: public-websites
```
