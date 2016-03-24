# test-network-modules

Playbooks for testing Ansible network modules

```
$ ansible-playbook all.yaml
```

To filter a set of test cases set limit_to to the name of the group (i.e. command, section, eapi, etc.): 

```
$ ansible-playbook all.yaml -e "limit_to=eos_command"
```

To filter a singular test case set the tags options to eapi or cli, set limit_to to the test group,
and test_cases to the name of the test:  

```
$ ansible-playbook all.yaml --tags="cli" -e "limit_to=eos_command test_case=notequal"
```

## Contributing Test Cases 

Test cases are added to roles based on the module being testing. Test cases
should include both `cli` and `nxapi` test cases. Cli test cases should be
added to role/tests/cli and eapi tests should be added to
role/tests/eapi.

### Conventions

- Each test case should generally follow the pattern:

  >setup —> test —> assert —> test again (idempotent) —> assert —> done

  This keeps test playbooks from becoming monolithic and difficult to
  troubleshoot.

- Include a name for each task that is not an assertion. (It's OK to add names
  to assertsion too. But to make it easy to identify the broken task within a failed
  test, at least provide a helpful name for each task.)

## License

Provided under the [GPLv3](https://github.com/ansible-testing/test-eos/blob/master/LICENSE) license. 

## Authors

Created and sponsored by [RedHat | Ansible](http://ansible.com).

