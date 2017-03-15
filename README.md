# SSP Cloud Application Template

This repo is a template to aid the documentation of a cloud application's SSP documentation.

### NIST-800-53 requirements

The requirements laid out in this template aim to satisfy a subset of the [NIST-800-53](https://github.com/opencontrol/NIST-800-53-Standards) compliance standard. While the entire NIST control set could be defined for the software application level, the reality is that many of the requirements are covered at the network/system level.  As a result, this repo attempts to identify the controls appropriate for introducing an application to an existing platform.

### OpenControl

We're utilizing the OpenControl format for compliance documentation.

The yaml format of the documentation should abide by the schema defined in the [opencontrol/schemas repo](https://github.com/opencontrol/schemas). There are several examples in that README for additional guidance.

With a properly formatted schema, we can feed the compliance documentation into the AWS SSP template using the following two projects:

- [Compliance Masonry](https://github.com/opencontrol/compliance-masonry)
- [FedRAMP Templater](https://github.com/opencontrol/fedramp-templater)

### Instructions

To utilize the template:

- Clone the repo
- Rename all the Policy directories to include your app name.  For example, for a fictional tool called 'otis':

      for file in `ls | grep Policy | awk -F_ '{print $1 "_" $2}'`; do mv ${file}_appname ${file}_otis; done

- Update the opencontrol.yaml file to include the new app name and description
- For each policy folder, edit the component.yaml to include the new appname at the top
- For each policy folder, populate the `implementation_status` and `text` fields for the control
  - Valid values for `implementation_status` are detailed [here](https://github.com/opencontrol/schemas/blob/master/kwalify/component/v3.0.0.yaml#L94)
  - Guidance for yaml syntax (e.g. multi-line strings with '>') are available [here](http://yaml.org/spec/1.2/spec.html) 
