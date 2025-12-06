# ansible-role-paperless-ngx

=======================
Paperless - the best home-hosted document management system: [Documentation paperless-ngx](https://docs.paperless-ngx.com/)

This role configures all aspects of the paperless container

## Tasks in Role

- Create Correspondents
- Create Tags
- Create Document Types
- Create Workflows
- Create Storage Paths
- Create Custom Field
- Performs Document Title Cleansing
- Set OCR parameters
- Creates a CIFS mount for your consume folder

Work in progress!

Commands used to export the documents:

```bash
document_exporter ../export -f -nt -d -p
```

Or, to include thumbnails:

```bash
document_exporter ../export -f -d -p
```

Command to import:

```bash
document_importer ../export
document_thumbnails
```

## Requirements

- `cifs-utils`
- Debian-based installation of paperless, through docker compose (a compose-file is provided in the project)

## Role Vars

name | description | default |
-----|-------------|---------|
| auth_token  | API token with full admin access to paperless  | none |
| ppl_endpoint | API URL for your paperless install | http://localhost:8010/api/ |
| delete_all_doc_types | Flag to prune DB of existing doc-types before creating new | false |
| cleansetag | Tag name used to monitor document title cleansing | is_cleansed |
| cifs_path | fstab path to your mount point for the consume folder | /media/SCANS |
| cifs_src | fstab src for the consume-folder | | 192.168.1.111/SCANS |
| ppl_owner | User id (number) for the main admin user | 3 |
| doc_types | list containing doctypes, matchingtype to be created | ... |
| correspondents | list containing correspondents, matchingtype to be created | ... |
| ppl_tags | list containing tags to be created | ... |
| storagepaths | list containing storagepaths to be created | ... |
| consumption_workflows | list containing workflows to be created | ... |

*See main.yml under 'defaults' for a complete list and more description*

# Running the role

```

```

## Playbook example

---

```
- hosts: myhosts
  become: true
  vars:
    pip_install_packages:
      - name: docker
  vars_files:
    - vars/portainer.yml
  roles:
   - geerlingguy.docker
   - geerlingguy.pip
   - waal70.paperless-ngx
```

## License

-------

[GPLv3](https://www.gnu.org/licenses/gpl-3.0.html#license-text)

## Author Information

-------

Unless otherwise noted, this entire repository is (c) 2025 by André (waal70). [See github profile](https://github.com/waal70)

Please contact me if you need a commercial license for any of these files
