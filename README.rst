1. Clone the git project

   .. code-block::
   
      git clone https://github.com/jpforcioli/ansible_ips_csv_to_fmg.git

2. Create and activate a python virtual environment

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
   credentials, ADOM, IPS and FIREWALL ADDRESS CSV files, etc.:

   .. code-block::

      ansible_host: 10.210.35.200
      ansible_user: ansible
      ansible_password: fortinet
      adom_name: ansible_ips_csv_to_fmg
      ips_csv_file: ${PWD}/ips_sig_samples.csv
      firewall_address_csv_file: ${PWD}/firewall_address_samples.csv

5. IPS CSV file should have the following format:

   .. code-block::

      name@sig

   For instance:

   .. code-block::

      SID77600858@F-SBID( --name "SID77600858"; --protocol tcp; --flow from_server; --pattern "<p>Companies-Best-Man-Vendors-Best</p>"; )

   where ``name`` is ``SID77600858`` and ``sig`` is ``F-SBID( --name
   "SID77600858"; --protocol tcp; --flow from_server; --pattern
   "<p>Companies-Best-Man-Vendors-Best</p>"; )``. 

6. FIREWALL ADDRESS CSV file should have the following format:

   .. code-block::

      name,subnet,color,comment

   For instance:
   
   .. code-block::     

      host_001,10.0.0.1/32,11,this is firewall address 1
      host_002,10.0.0.2/32,11,this is firewall address 2
      host_003,10.0.0.3/32,11,this is firewall address 3

6. To run the ansible playbook

   .. code-block::

      # To load the IPS SIG CSV into FMG
      ansible-playbook -i inventory.yml ips_sig_to_fmg.yml

      # To load the FIREWALL ADDRESS CSV into FMG
      ansible-playbook -i inventory.yml firewall_address_to_fmg.yml