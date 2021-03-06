# Firebase Realtime-database backup client

[![Current version](https://img.shields.io/github/release/stayapp-corp/firebase-realtime-database-backup.svg)](https://packagist.org/packages/stayapp-corp/firebase-realtime-database-backup)
[![Supported PHP version](https://img.shields.io/packagist/php-v/stayapp-corp/firebase-realtime-database-backup.svg)]()
[![Total Downloads](https://img.shields.io/packagist/dt/stayapp-corp/firebase-realtime-database-backup.svg)](https://packagist.org/packages/stayapp-corp/firebase-realtime-database-backup/stats)
[![License](https://img.shields.io/github/license/stayapp-corp/firebase-realtime-database-backup.svg)](https://github.com/stayapp-corp/firebase-realtime-database-backup/blob/master/LICENSE)

[![GitHub stars](https://img.shields.io/github/stars/stayapp-corp/firebase-realtime-database-backup.svg?label=Stars&style=social)](https://github.com/stayapp-corp/firebase-realtime-database-backup/stargazers)
[![GitHub watchers](https://img.shields.io/github/watchers/stayapp-corp/firebase-realtime-database-backup.svg?label=Watch&style=social)](https://github.com/stayapp-corp/firebase-realtime-database-backup/watchers)

Available on [Packagist](https://packagist.org/packages/stayapp-corp/firebase-realtime-database-backup).

## Description

Unfortunately, the firebase backup service is only today available for Blaze plan and you can not do backups more than one time per day.

The manual export button available on cli (that uses the rest endpoint) doesn't work for bigger databases. This library permits to export and import the firebase realtime-database using the rest api and a division strategy to enable the capability to export and import bigger databases.

### Adding this to your project using Composer

In some situations, is a good idea to install this library in your project and use our processor classes to make your own backup in your service. To do that you can install this library using composer:

```
$ cd <your_project>
$ composer require stayapp-corp/firebase-realtime-database-backup
```

More info about Composer at [getcomposer.org](http://getcomposer.org).

### Using this library by Console CLI

#### Database Export

```
./frdbackup export --project_id <firebase project id> --project_key <firebase REST access key>
```

There are some optional parameters:

| Long parameter | short parameter | Description | Default value |
| --- | --- | --- | --- |
| temp_dir | t | Temporary directory to save all downloaded database files before creating .tar.gz backup file | ./temp |
| max_ipp | i | The maximum size of items per page that some query to the database will use. Note that if you specify a very large number and you have nodes that can't get this quantity of samples, the script can take a long time to finish because it will be decrease the IPP size until it can get the data. | 1000 |
| output_file | o | Compressed backup (.tar.gz) output file path  | ./backups/BACKUP-<ACTUAL_DATE> |

#### Database Import

```
./frdbackup import --project_id <firebase project id> --project_key <firebase REST access key> --backup_file <path to .tar.gz backup file>
```
