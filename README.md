# libsys

A Library Management Web App.

It allows a librarian to track:
 * `books` and their `quantity`,
 * `members`,
 * `books issued to members`,
 * `book fees`,
 * `transactions`.

## Use Cases

* Perform CRUD operations on Books and Members.
* Issue a book to a member.
* Issue a book return from a member.
* Search for a book by name and author.
* Charge a rent fee on book returns.
* Make sure a member’s outstanding debt is not more than KES. 500.

## Install Dependencies

Ideally, you should run Debian 12+ or Ubuntu 22+ so you don't have issues with some of the packages.

* Update your system's package index:
    ``` bash
    sudo apt update
    ```

* Install `git`, `python`, `redis`, and `MariaDB`:
    ``` bash
sudo apt install git python-is-python3 python3-dev python3-pip redis-server libmariadb-dev mariadb-server mariadb-client pkg-config
    ```

* If, during setup, you were not prompted to set the MySQL root password, run this command to initalize the MySQL server setup:
    ``` bash
    mariadb-secure-installation
    ```

* Edit the MariaDB config file. This applies only if you're using Frappe v15.20 and below:
    ``` bash
    nvim /etc/mysql/my.cnf
    ```

* Add this config:
        ``` bash
        [mysqld]
        character-set-client-handshake = FALSE
        character-set-server = utfmb4
        collation-server = utfmb4_unicode_ci

        [mysql]
        default-character-set = utfmb4
        ```

* Restart the MariaDB service:
    ``` bash
    sudo systemctl restart mariadb
    ```

* Install [`node`](https://github.com/creationix/nvm)

* Install `yarn`:
    ``` bash
    npm install -g yarn
    ```

* Install wkhtmltopdf for pdf generation:
    ``` bash
    sudo apt install xvfb libfontconfig
    ```
    
    Download and install [wkhtmltopdf](https://wkhtmltopdf.org/downloads.html), then run this command:
    ``` bash
    sudo dpkg -i wkhtmltox_file.deb
    ```

## Get Started

Let's set up our developer environment.

### Set Up the Python Virtual Environment

Navigate to the project directory and run the following command:
    ``` bash
    python -m venv env
    ```

After creating the virtual environment, you activate it by running:
    ``` bash
    source env/bin/activate
    ```

Once activated, you can install packages using `pip` without breaking the global system config. To deactivate the virtual environment, run:
    ```bash
    deactivate
    ```

To install any packages via pip, add them to the requirements.txt file and run:
    ``` bash
    pip install -r requirements.txt
    ```
The `requirements.txt` file lists all the dependencies your project relies on.

