tensorflow
==========

This role install tensorflow on Linux(CentOS and Ubuntu are supported).

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

There are only two variables for repository mirror, as the default values listed below:

    # The venv path to install tensorflow
    tensorflow_venv_path: ~/venvs/tensorflow
    
    # The binary url of tensorflow
    TF_BINARY_URL_Linux_CPU_2: https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.12.0rc0-cp27-none-linux_x86_64.whl

Usually you don't need to change them.

Dependencies
------------

This role depend on [frank6866.pip](https://galaxy.ansible.com/frank6866/pip/)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: frank6866.pip }
         - { role: frank6866.tensorflow }

License
-------

MIT

