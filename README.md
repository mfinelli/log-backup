# Log Backup

Backup rotated logfiles to AWS S3.

## Dependencies

### s3cmd

[s3cmd](https://github.com/s3tools/s3cmd) is used to actually upload the
backups to AWS, so you will need to install and configure it first. Install
it with your favorite package manager and then configure with:

```shell
$ s3cmd --configure
```

## Configuration

Configuration for the backup is saved in your home directory in the
`.logbackup` file. It is basically another bash script that defines the
required variables and then gets sourced before the backup runs.

You must define an encryption passphrase, the s3 bucket to use, and the log
patterns and prefixes to use when uploading.

```shell
# Choose a long, strong password to encrypt the files.
PASSPHRASE="AReallyGoodPassword"

# List of paths/patterns (wildcards) to backup:
LOGPATHS=('/var/log/app1/*.gz' '/var/log/app2/*.gz')

# List of "folders" in which to store each log path:
PREFIX=('app1' 'app2')

# List your buckets with `s3cmd ls`.
BUCKET="your-backup-bucket"
```
