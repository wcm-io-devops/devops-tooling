## Debugging Ansible Automation for AEM

Hints for debugging the [Automation for AEM][ansible-aem].


### Ansible verbose mode

Ansible Commands support the verbose flag

```
-v # simple verbose output
-vv # more verbose
-vvv # even more verbose
-vvvv # connection debugging
-vvvvv # even more verbose, and so on
```

Which each added "v" the verbosity increases (and the readability decreases).

It is recommened to write the output to a file like:

```
ansible-playbook playbook-setup-prod.yml | tee ansible.log
```

### Use \-\-skip-tags

If you want to speed up debugging and want to skip the tasks/roles that are working use the parameter 

```
--skip-tags aem-cms,aem-dispatcher
```

When working with the Conga Ansible IT Automation it is recommended to skip the compile process of the wcm_io_devops.conga_maven role to save time

```
--skip-tags conga-maven-compile
```

For more information refer to: https://docs.ansible.com/ansible/2.6/user_guide/playbooks_tags.html

### Use \-\-start-at-task

If you want to start the playbook at a particula task you can use the --start-at-task option:

```
ansible-playbook playbook-setup-prod.yml --start-at-task="Download AEM quickstart."
```

### Execute interactively

If you want to inspect the result of each task you can run the playbook with the --step option:

```
ansible-playbook playbook-setup-prod.yml --step
```

This will cause Ansible to stop on each task if it should execute that task.

### Enable debug logs

Ansible is for example hiding the Maven log output. When an error occurs the log-output will be shown.

#### wcm_io_devops.conga_aem_packages

This role supports the logging of the current maven output to a file which then can be "tailed".

Refer to:

* https://github.com/wcm-io-devops/ansible-conga-aem-packages and
* https://github.com/wcm-io-devops/ansible-conga-aem-packages/blob/master/defaults/main.yml#L27-L31

For more information.

## Advanced Debugging

### Manipulating Roles

Ansible looks per default in the following pathes to search for roles

* `roles` directory, relative to the playbook file.
* By default, in `/etc/ansible/roles`

This behavior becomes handy when you want to debug a role in your current project.

#### Example for wcm_io_devops.conga_aem_packages role

_Prepare role for local manipulation_
```
# switch into the ansible playbook dir
mkdir roles && cd roles
git clone https://github.com/wcm-io-devops/ansible-conga-aem-packages.git && git checkout 1.0.0
```

With this setup the role "wcm_io_devops.conga_aem_packages" will be loaded from the roles directory.

You can then start manipulating the role e.g. by adding debug statements, manual inputs and fail statements to avoid continuing of the play.

_Example: Output content of conga_config and continue_

```yaml
- name: Debug conga_config
  debug:
    msg:
      - conga_config
      - "{{ conga_config }}"
 
- fail:
    msg: do not continue
```

_Example: Wait for user input_

```yaml
- name: "Wait for user input"
  prompt: "Continue?"
```

Links:

* https://docs.ansible.com/ansible/2.6/modules/fail_module.html
* https://docs.ansible.com/ansible/2.6/modules/debug_module.html
* https://docs.ansible.com/ansible/2.6/user_guide/playbooks_prompts.html


### Playbook Debugger

When you are using Ansible 2.5+ you can use the Playbook Debugger<br/>
https://docs.ansible.com/ansible/2.5/user_guide/playbooks_debugger.html


[ansible-aem]: http://devops.wcm.io/ansible-aem/
