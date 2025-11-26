# msfconsole

## Overview

- **msfconsole** is the only supported way to access most of the features within Metasploit.
- Provides a console-based interface to the framework.
- Contains the most features and is the most stable MSF interface.
- Full readline support, tabbing, and command completion.
- Execution of external commands in msfconsole is possible.

---

## msfconsole Usage and Commands

### Default Installation Path

Shows the default installation path of the Metasploit Framework on a typical Linux system:

    /usr/share/metasploit-framework/

### Installation

Installs the Metasploit Framework package using the system package manager:

    apt install metasploit-framework


### PostgreSQL Setup

Starts and enables the PostgreSQL service, which is required for Metasploit's database features:

    systemctl start postgresql.service
    systemctl enable postgresql.service


Verifies that PostgreSQL is running and listening on the expected ports using `netstat` or `ss`:

    netstat -nltup | grep postgres
    ss -nltup | grep postgres


### Database Management

Manages and initializes the Metasploit database using `msfdb`:

    msfdb
    msfdb init

Displays the Metasploit database configuration file, showing database names, users, and connection parameters:
cat /usr/share/metasploit-framework/config/database.yml

Example `database.yml` file:

    development:
    adapter: postgresql
    database: msf
    username: msf
    password: OZVT0N7Mp4p2nbVUMx4krV6+XAKSlbTvdEHD9nMiSEU=
    host: localhost
    port: 5432
    pool: 5
    timeout: 5
    
    production:
    adapter: postgresql
    database: msf
    username: msf
    password: OZVT0N7Mp4p2nbVUMx4krV6+XAKSlbTvdEHD9nMiSEU=
    host: localhost
    port: 5432
    pool: 5
    timeout: 5
    
    test:
    adapter: postgresql
    database: msf_test
    username: msf
    password: OZVT0N7Mp4p2nbVUMx4krV6+XAKSlbTvdEHD9nMiSEU=
    host: localhost
    port: 5432



---

## Starting msfconsole

Launches msfconsole in normal mode, quiet mode, or displays CLI help:
     
      msfconsole
      msfconsole -q
      msfconsole -h



---

## Help and Listing Commands

Shows how to get general help and a list of commands from within msfconsole:
  
    msf6 > ? # To get help and command list
    msf6 > help # To get help and command list


Shows help for the `show` command and lists different types of modules and components:
   
    msf6 > show -h # Help for 'show'
    msf6 > show all # List all components
    msf6 > show encoders # List all encoders
    msf6 > show exploits # List all exploits
    msf6 > show payloads # List all payloads
    
    text

---

## Searching Modules

Provides help for the `search` command and demonstrates different ways to search modules by keyword, name, type, author, or check support.

Shows help for the `search` command using the long form help syntax inside msfconsole:

    help search

Shows help for the `search` command using its own `-h` (help) option:

    search -h

- Searches for all modules related to the SMB protocol (any module whose name, description, or references match `smb`):

      search smb


- Searches for modules whose descriptive `name` field contains `smb`:

      search name:smb

- Searches specifically for modules of type `payload` that are related to Meterpreter:

      search meterpreter type:payload


- Searches for modules of type `payload` that are related to SMB:

      search smb type:payload

- Searches for modules whose descriptive name contains `sql` (such as SQL-related exploits, auxiliary modules, etc.):

      search name:sql

- Searches for modules written by the author `dookie`:

      search author:dookie

## Advanced Search and Module Management

### Searching for Modules with Pre-Exploitation Check

- Searches for modules that implement a `check` method (`check:Yes` means support for pre-exploitation check):
    ```
    search check:Yes
    ```

- Searches for SMB-related modules that also have a `check` method available:
    ```
    search smb check:Yes
    ```

### Selecting and Using Exploit Modules

- Selects an exploit module by index or full path and shows how to go back to the main prompt:
    ```
    search ms08_067_netapi
    use 5
    back
    use exploit/windows/smb/ms08_067_netapi
    ```

### Viewing Exploit Options and Info

- Displays configurable options and detailed information for the current exploit module:
    ```
    msf6 exploit(windows/smb/ms08_067_netapi) > show options
    msf6 exploit(windows/smb/ms08_067_netapi) > show info
    ```

---

## Metasploit Database Management

- Getting help, checking status, and manual connection:
    ```
    help database
    db_status
    db_connect user:pass@127.0.0.1/metasploit3
    ```

### Workspace Management

- Commands to manage workspaces for different engagements or projects:
    ```
    workspace -h
    workspace -a armour
    workspace -a infosec
    workspace -d infosec
    workspace armour
    ```

---

## Nmap Integration

- Running Nmap scans via `db_nmap` and storing results in the database:
    ```
    db_nmap -sn 192.168.1.1/24
    db_nmap -v -sT -p- 192.168.1.31
    db_nmap -v -sT -sV -p- -A 192.168.1.212
    ```

---

## Host Management

- Listing, filtering, naming, and annotating hosts in the database:
    ```
    hosts
    hosts -h
    hosts -d 192.168.1.200
    hosts -n kali 192.168.1.1
    hosts -i "My kali" 192.168.1.6
    hosts -m "Dont Scan" 192.168.1.6
    hosts -c address
    hosts -c address,os_name
    hosts -a 192.168.1.200
    hosts -S Windows
    ```

---

## Viewing Service Information

- Viewing and filtering services discovered during scans:
    ```
    services
    services -h
    services -p 80
    ```

---

## Database Queries

- Show all hosts in the database:
    ```
    hosts
    ```

- Show hosts exploited successfully:
    ```
    hosts -R
    ```

- Show hosts scanned during engagement:
    ```
    hosts -T
    ```

- Show credential information:
    ```
    creds
    ```

- Show loot/evidence collected:
    ```
    loot
    ```

- Show services discovered:
    ```
    services
    ```

- Show vulnerabilities discovered:
    ```
    vulns
    ```

- Show notes from scans:
    ```
    notes
    ```

## Metasploit `services` Command

Views and filters service information discovered during scans.

### Basic Usage

- Shows help and all available options for the command.
    ```
    services -h
    ```

- Lists all known services (ports, states, names, etc.) from the database.
    ```
    services
    ```

### Filter by Port

- Shows only services running on port 80 (typically HTTP).
    ```
    services -p 80
    ```

- Shows only services on port 445 (often SMB).
    ```
    services -p 445
    ```

### Filter by Host

- Shows all services associated with host `192.168.1.31`
    ```
    services 192.168.1.31
    ```

---

## Select Columns

- Limits the output to just the port and state columns for each service.
    ```
    services -c port,state
    ```

---

## Working with Exploits, Data, Credentials, Loot, and Sessions

### Load an Exploit Module

- Selects and loads the `ms08_067_netapi` exploit module for the MS08-067 Windows SMB vulnerability.
    ```
    use exploit/windows/smb/ms08_067_netapi
    ```

### View Vulnerabilities

- Lists vulnerabilities stored in the database, typically populated from scans or exploitation results.
    ```
    vulns
    ```

---

## Import Scan Data

- Imports external scan results (for example, Nmap/Nessus XML) into the Metasploit database so hosts, services, and vulns appear under `hosts`, `services`, and `vulns`.
    ```
    db_import /home/armour/vm/192.168.1.244/192.168.1.244_ver_sc.xml
    ```

---


## Export Database Data

- Shows help and options for exporting database contents (formats, output path, etc.).
    ```
    db_export -h
    ```

- Exports the current workspace database (hosts, services, vulns, loot) to an XML file.
    ```
    db_export -f xml /home/armour/vm/msf_host.xml
    ```

---

## View Stored Credentials

- Displays all credentials captured or imported (usernames, passwords, hashes, related services).
    ```
    creds
    ```

---

## View Loot

- Lists loot files and data (config files, dumps, captured documents, etc.) stored from post-exploitation modules.
    ```
    loot
    ```

---

## Manage Sessions

- Shows help and usage options for session management (list, interact, kill, background, etc.).
    ```
    sessions -h
    ```

- Lists all active sessions with IDs, types (meterpreter/shell), hosts, and users.
    ```
    sessions -l
    ```

- Interacts with the session having ID 1, attaching your console to that shell or Meterpreter session.
    ```
    sessions -i 1
    ```

