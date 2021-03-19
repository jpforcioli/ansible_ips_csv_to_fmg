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
   credentials, ADOM, IPS CSV file, etc.:

   .. code-block::

      ansible_host: 10.210.35.200
      ansible_user: ansible
      ansible_password: fortinet
      adom_name: ansible_ips_csv_to_fmg
      ips_csv_file: ${PWD}/ips_sig_samples.csv

5. IPS CSV file should have the following format:

   .. code-block::

      name@sig

   For instance:

   .. code-block::

      SID77600858@F-SBID( --name "SID77600858"; --protocol tcp; --flow from_server; --pattern "<p>Companies-Best-Man-Vendors-Best</p>"; )

   where ``name`` is ``SID77600858`` and ``sig`` is ``F-SBID( --name
   "SID77600858"; --protocol tcp; --flow from_server; --pattern
   "<p>Companies-Best-Man-Vendors-Best</p>"; )``. 