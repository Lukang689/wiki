### svn备份脚本

```
# SVN备份脚本
#!/bin/sh
# project repo backup script

logFile=/root/svnBackup/svnbak.log
DATE=`date +%Y%m%d`
BakDir=/root/svnBackup
SvnDir=/svn/project
SVNADMIN=/svn/root/bin/svnadmin

echo "" >> $logFile
echo " " >> $logFile
echo "-------------------------------------------" >> $logFile
echo $(date +"%y-%m-%d %H:%M:%S") >> $logFile
echo "-------------------------------------------" >> $logFile

cd $BakDir

project=project1.0
projectdata=$SvnDir/$project
destdir=$BakDir/$project
dumpfile=$DATE.$project.tgz

if [ -f $BakDir/$dumpfile ]
then
echo "backup file have exist.Exit!" >>$logFile
else
$SVNADMIN hotcopy $projectdata $destdir --clean-logs
tar -Pczvf $dumpfile $destdir > /dev/null
rm -fr $project
echo "backup $project done into $dumpfile ">>$logFile
fi

oldfile="$BakDir/"$(date +%y%m%d --date='28 days ago').$project.tgz

if [ -f $oldfile ]
then
rm -f $oldfile >> $logFile 2>&1
echo "[$oldfile]Delete Old File Success!" >> $logFile
else
echo "[$oldfile]No Old Backup File!" >> $logFile
fi

# 定时执行,每天23:30执行一次脚本
crontab -e
30 23 * * * /root/svnbak.sh
```

