[![CI](https://github.com/de-it-krachten/ansible-role-html_report/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-html_report/actions?query=workflow%3ACI)


# ansible-role-html_report

Creates basic HTML reports from YAML or CSV files.<br>
Reports can be sorted and filtered.<br>
See https://datatables.net



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- Red Hat Enterprise Linux 10<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- RockyLinux 10
- OracleLinux 8
- OracleLinux 9
- OracleLinux 10
- AlmaLinux 8
- AlmaLinux 9
- AlmaLinux 10
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Debian 13 (Trixie)
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 42
- Fedora 43

Note:
<sup>1</sup> : no automated testing is performed on these platforms


## Role Variables
### defaults/main.yml
<pre><code>
# jquery & datatables setings
html_report_datatables_css: https://cdn.datatables.net/2.3.7/css/dataTables.dataTables.css
html_report_datatables_js: https://cdn.datatables.net/2.3.7/js/dataTables.js
html_report_jquery: https://code.jquery.com/jquery-3.7.1.js

# File to convert into HTML report
# html_report_file: /tmp/report.csv

# Provide data sugin a variable instead of file
# html_report_data: [ { 'f1': 'x', 'f2': 'y' } ]

# File location to place the report
# html_report_path: /tmp/report.html

# Name of the table
# html_report_table_name: TEST

# Template to use for creating the HTML report
html_report_template: table.html.j2

# Convert field that start with http/https into links
html_report_link: true
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'html_report' pre playbook
  ansible.builtin.import_playbook: converge-pre.yml
  when: molecule_converge_pre is undefined or molecule_converge_pre | bool
- name: sample playbook for role 'html_report'
  hosts: all
  become: 'yes'
  vars:
    molecule_driver: '{{ lookup(''env'', ''MOLECULE_DRIVER_NAME'') }}'
    html_report_path: /tmp/customers.html
    html_report_file: /tmp/customers-100.csv
    html_report_table_name: TEST
  tasks:
    - name: Include role 'html_report'
      ansible.builtin.include_role:
        name: html_report
</pre></code>
