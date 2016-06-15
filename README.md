ansible-role-hosts-inventory
=========

Populates a file ( /etc/hosts ) based on ansible groups

Requirements
------------

Before this role runs you also needs to gather facts for the group which you are writing to a hosts file.

Alternatively you can use data specified for each host to populate the hosts file.

Role Variables
--------------

See defaults/main.yml for the actual list

<pre>
hosts_file_ansible_group_to_hosts_file: "{{ groups.all }}"
hosts_file_to_populate: "/tmp/hosts"
# ip_match: look for this string in the IP address
hosts_file_ip_match: "10.11"
# the number of ipv4_addresses (elements in ansible_all_ipv4_addresses in each host in hosts_file_ansible_group_to_hosts_file)
hosts_file_num_interfaces: [ 0, 1, 2, 3, 4 ]
</pre>

 - If your machines have more than 5 ipv4_addresses add some numbers to the hosts_file_num_interfaces list
 - Change hosts_file_ip_match to match the IP addresses you want to add to the hosts file

To use data defined for the hosts as a source of the data you can specify the following variables.

<pre>
hosts_ip_source: "hostdata"
ipaddress_source_var: "ip_address"
</pre>

To use data defined for the hosts and template as a source of the data you can specify the following variables.

<pre>
hosts_ip_source: "template"
ipaddress_source_var: "ip_address"
</pre>

Dependencies

Dependencies
------------

None, but this could be used with dnsmasq like https://github.com/CSC-IT-Center-for-Science/ansible-role-dnsmasq

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: gather_facts
      hosts: all
      tasks: [ ]

    - hosts: dns_servers
      roles:
         - { role: ansible-role-dnsmasq }
         - { role: ansible-role-hosts-inventory }

License
-------

MIT

Author Information
------------------
