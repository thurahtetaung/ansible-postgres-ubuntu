# Setting up a PostgreSQL database on Ubuntu 22.04 using Ansible

## Prerequisites

- Ansible 2.15 or later
- Ubuntu 22.04 on the target host
- A user with sudo privileges on the target host
- A passwordless SSH connection to the target host

## Usage

1. Clone this repository
2. Edit the `inventory` file to include the IP address and username of the target host. You can include multiple hosts if you wish to set up multiple databases.
3. Test the connection to the target host using the `ping` module:

    ```bash
    ansible -i inventory all -m ping
    ```

4. Modify the `vars.yml` file to include the desired database name, user, and password
5. Modify the `seed.sql` file to include the desired database schema
6. Run the playbook:

    ```bash
    ansible-playbook -i inventory playbook.yml
    ```
7. Verify that the database was created by connecting to the server via ssh and running the following command:

      ```bash
      psql -U <user> -d <database> -c "SELECT * FROM users;"
      ```
