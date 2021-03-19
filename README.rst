1. Clone the git project

   .. code-block::
   
      git clone https://github.com/jpforcioli/ansible_ips_csv_to_fmg.git

2. Create and enter a python virtual environment

   .. code-block::

      cd ansible_ips_csv_to_fmg
      python3 -m venv .venv
      source .venv/bin/active

3. Install the project's requirements


   .. code-block::

      pip install -r requirements.txt
      ansible-galaxy collection install fortinet.fortimanager

4. Edit the ``inventory.yml``

   You have to update the variables describing your FortiManager IP and
   credentials, ADOM, etc.:

   .. code-block::

      ansible_host: 10.210.35.200
      ansible_user: ansbible
      ansible_password: fortinet
      adom_name: ansible_ips_csv_to_fmg

      