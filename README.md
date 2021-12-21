# ansible_notes
#######################################
### Ansible play to install packages###
#######################################
- name: Play for Installing packages
  hosts: all
  ignore_errors: true
  become: yes
  vars:
    packages:
    - name: apache
      required: true
    - name: mysql
      required: true
    - name: httpd
      required: false
  tasks:
  - name: Install "{{ item.name }}" on DEB
    apt:
      name: {{ item.name }}"
      state: present
    when: item.required==true
    loop: "{{ packages }}"
    
 >> mail module
 ###############
 
 - mail
     to: suneel.raghavaraju@kyndryl.com
     subject: test from tower
     body: This is test
     
 >> register usage
 ##################
 
 register: result
 
 when: result.stdout.find('down') != -1
