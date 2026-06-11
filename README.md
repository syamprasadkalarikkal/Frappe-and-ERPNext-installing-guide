# Frappe-and-ERPNext-installing-guide
# ERPNext v15 Installation Guide (Ubuntu)

## 1. Update System

```bash
sudo apt update
sudo apt upgrade -y
```

**Why?**

* `apt update` refreshes the package list from Ubuntu repositories.
* `apt upgrade` installs the latest security and software updates.

---

## 2. Install Git

```bash
sudo apt install git -y
```

**Why?**

Git is a version control system. Bench uses Git to download and update Frappe and ERPNext source code.

---

## 3. Install Python Development Tools

```bash
sudo apt install python3-dev python3-pip python3-venv -y
```

**Why?**

* `python3-dev` → Required to build Python packages.
* `python3-pip` → Python package manager.
* `python3-venv` → Creates isolated Python environments.

ERPNext backend is built with Python.

---

## 4. Install MariaDB

```bash
sudo apt install mariadb-server mariadb-client -y
```

**Why?**

MariaDB stores all ERPNext data such as customers, invoices, stock, and accounts.

* `mariadb-server` → Database server.
* `mariadb-client` → Command-line tool to access the database.

---

## 5. Configure MariaDB

```bash
sudo nano /etc/mysql/my.cnf
```

**Why?**

ERPNext requires UTF-8 character encoding to properly store all languages and special characters.

---

## 6. Install Redis

```bash
sudo apt install redis-server -y
```

**Why?**

Redis is an in-memory database used for:

* Cache management
* Background jobs
* Real-time notifications
* Performance improvements

---

## 7. Install Node.js

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install nodejs -y
```

**Why?**

Node.js builds ERPNext's frontend assets such as JavaScript, CSS, and web pages.

---

## 8. Install Yarn

```bash
sudo npm install -g yarn
```

**Why?**

Yarn downloads and manages JavaScript dependencies required by Frappe and ERPNext.

---

## 9. Install wkhtmltopdf

```bash
sudo apt install wkhtmltopdf -y
```

**Why?**

ERPNext uses wkhtmltopdf to generate PDF files for:

* Invoices
* Quotations
* Purchase Orders
* Reports

---

## 10. Install Frappe Bench

```bash
pip3 install frappe-bench
```

**Why?**

Bench is the command-line tool used to:

* Create ERPNext sites
* Install apps
* Run development servers
* Update ERPNext

---

## 11. Initialize Bench

```bash
bench init frappe-bench
```

**Why?**

Creates the Frappe environment and project structure required for ERPNext development.

---

## 12. Create a Site

```bash
bench new-site mysite.local
```

**Why?**

Creates a new ERPNext database and website instance.

Each company/site can have its own database.

---

## 13. Download ERPNext

```bash
bench get-app erpnext
```

**Why?**

Downloads ERPNext source code into the Bench environment.

---

## 14. Install ERPNext

```bash
bench --site mysite.local install-app erpnext
```

**Why?**

Installs ERPNext modules such as:

* Accounts
* CRM
* HR
* Stock
* Manufacturing

into your site.

---

## 15. Start Development Server

```bash
bench start
```

**Why?**

Starts all required services:

* Web server
* Redis
* Scheduler
* Background workers

and makes ERPNext accessible in the browser.

Open:

```text
http://localhost:8000
```

---

## Useful Commands

### Backup Database

```bash
bench --site mysite.local backup
```

Creates a backup of your ERPNext database and files.

### Migrate Site

```bash
bench --site mysite.local migrate
```

Applies database updates after app changes.

### Update ERPNext

```bash
bench update
```

Downloads and installs the latest updates.

### Restart Bench

```bash
bench restart
```

Restarts ERPNext services.

