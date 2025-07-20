<script>
  function multiplyBy()
  {
    num1 = document.getElementById(
      "firstNumber").value;
    num2 = document.getElementById(
      "secondNumber").value;
    document.getElementById(
      "result").innerHTML = num1 * num2;
  }
</script>

## Backing up the RMM

!!!note
    This is only applicable for the standard install, not Docker installs.

A backup script is provided for quick and easy way to backup all settings/data into one file to migrate to another server.

!!!warning
    The backup script does **not** self update itself. Always make sure you have latest version from the [master](https://github.com/nuvemquery/tacticalrmm/blob/master/backup.sh) branch by verifying the `SCRIPT_VERSION` at the top of the file matches.

Make sure you are logged into the user you used to install TRMM eg `tactical`. Then download and run the backup script:

```bash
wget -N https://raw.githubusercontent.com/nuvemquery/tacticalrmm/master/backup.sh
chmod +x backup.sh
./backup.sh
```

The backup tar file will be saved in `/rmmbackups` with the following format:

`rmm-backup-CURRENTDATETIME.tar`

## Schedule to run Daily via Cron

!!!note
    You MUST enable [passwordless sudo](https://timonweb.com/devops/how-to-enable-passwordless-sudo-for-a-specific-user-in-linux/) for your linux user or you won't get all files backed up, do a dry run first before setting up a schedule! You should verify this also by doing a test restore or verify the files have content.

To schedule automated daily backups run the script with the `--schedule` flag

```bash
./backup.sh --schedule
```

This will do the following:

* Create daily, weekly and monthly folders under /rmmbackup.

* Schedule backups using cron to run at midnight every night.

* As well as Daily backups, there are monthly backups on the 10th day of every month and weekly backups every Friday.

* Automated pruning of backup files, daily kept for 2 weeks, weekly for 2 months and monthly for 1 year. To calculate estimated disk needs, take the size of a manual backup and * 37. eg 600MB backup * 37 = 22.2GB of space needed. <br>
 <form>
        Calculate Backup Size (in MB): <input type="text" id="firstNumber" style="background-color: #f0f0f0;  color: #000000; width: 100px;" />MB * <input type="text" id="secondNumber" style="background-color: #f0f0f0;  color: #000000; width: 30px;" value = "37" /> = <input type="button" onClick="multiplyBy()" Value="Calculate" style="background-color: #f0f0f0;  color: #000000;" /> Total Space needed <span id="result"></span>MB</form> 

!!!warning
    The backup script will just save to your server drive, you ideally want to automate moving this to another server. Please ensure you have space for the backups to be stored.

## Video Walkthru

<div class="video-wrapper">
  <iframe width="400" height="225" src="https://www.youtube.com/embed/rC0NgYJUf_8" frameborder="0" allowfullscreen></iframe>
</div>

## Backup Testing

See [Restore Testing](restore.md#restore-testing)
