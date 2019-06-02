## Ansible Automation for AEM

wcm.io DevOps provides a set of [Ansible][ansible] roles to automate infrastructure setup and configuration management for Adobe Experience Manager (AEM).

The Ansible roles are optimized to be used together with [CONGA][conga], but some can also be used standalone.

A good starting point for setting up AEM projects for deployment automation with CONGA and Ansible is using the<br/>
[wcm.io Maven Archetype for AEM Configuration Management][aem-configmgmt-archetype].

If anything goes wrong, have a look at [Debugging Ansible Automation for AEM][ansible-debugging].


### Roles on Ansible Galaxy

The Ansible roles are published on Ansibe Galaxy:

* [wcm.io DevOps Ansible roles on Ansible Galaxy][ansible-galaxy-roles]
* [wcm.io DevOps Ansible roles on GitHub][github-ansible-roles]


### Further Resources

* [adaptTo() 2017 Talk: Automate AEM Deployment with Ansible and wcm.io CONGA][adaptto-talk-2017-aem-ansible]
* [adaptTo() 2018 Talk: Maven Archetypes for AEM][adaptto-talk-2018-aem-archetypes] - about AEM project archetypes including Ansible/CONGA-based cloud deployment
* [Debugging Ansible Automation for AEM][ansible-debugging]



[ansible]: https://www.ansible.com/
[ansible-debugging]: ansible-debugging.html
[conga]: https://devops.wcm.io/conga
[aem-configmgmt-archetype]: https://wcm.io/tooling/maven/archetypes/aem-confmgmt/
[ansible-galaxy-roles]: https://galaxy.ansible.com/wcm_io_devops
[github-ansible-roles]: https://github.com/wcm-io-devops?q=topic%3Aansible-role
[adaptto-talk-2017-aem-ansible]: https://adapt.to/2017/en/schedule/automate-aem-deployment-with-ansible-and-wcm-io-conga.html
[adaptto-talk-2018-aem-archetypes]: https://adapt.to/2018/en/schedule/maven-archetypes-for-aem.html
