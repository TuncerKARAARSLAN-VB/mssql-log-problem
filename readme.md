# Minimize Log File

If your MSSQL Log file is too large, you can minimize your log file with the following steps

The following example uses the sample database name USANEWAGE. You should work with the problematic database name.

```mssql

use USANEWAGE;

BACKUP DATABASE USANEWAGE TO DISK = 'C:\temp\USANEWAGE.bak'

BACKUP LOG USANEWAGE TO DISK = 'C:\temp\USANEWAGE.trn'

EXEC sp_helpfile;

DBCC SHRINKFILE (USANEWAGE_log, 1);

ALTER DATABASE USANEWAGE SET RECOVERY SIMPLE;

DBCC SHRINKFILE (USANEWAGE_log, 1);

```
