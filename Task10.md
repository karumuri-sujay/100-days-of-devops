### Task:


The production support team of xFusionCorp Industries is working on developing bash scripts to automate different day-to-day tasks. One requirement is to create a bash script for taking website backups. They have a static website running on App Server 3 in Stratos Datacenter, and they need to create a bash script named `beta_backup.sh` to accomplish the following tasks:

**Objectives:**

1. Create a zip archive named `xfusioncorp_beta.zip` of the `/var/www/html/beta` directory
2. Save the archive in `/backup/` on App Server 3 (temporary storage, cleaned weekly)
3. Copy the created archive to the Nautilus Backup Server in the `/backup/` location
4. Ensure the script doesn't ask for a password when copying the archive file
5. The respective server user must be able to run the script

**Script Requirements:**

* Script location: `/scripts/beta_backup.sh` on App Server 3
* Must be executable by the server user
* Automated execution without user intervention
