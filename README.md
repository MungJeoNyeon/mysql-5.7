# mysql-5.7
error resolution

# Error: Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)

  ➜  ~ brew services restart mysql
  Stopping `mysql`... (might take a while)
  ==> Successfully stopped `mysql` (label: homebrew.mxcl.mysql)
  Error: Formula `mysql` is not installed.

  ➜  ~ brew uninstall mysql@5.7
  ➜  ~ rm -rf /opt/homebrew/var/mysql
  ➜  ~ brew list | grep mysql

  ➜  ~ brew install mysql@5.7


  ➜  ~ cat /usr/local/var/mysql/$(hostname).err

  ➜  ~ sudo chown -R $(whoami) /usr/local/var/mysql
  sudo chown -R $(whoami) /usr/local/opt/mysql@5.7

  ➜  ~ brew services restart mysql@5.7 

  ➜  ~ brew services list
  mysql@5.7               error  256 mac  ~/Library/LaunchAgents/homebrew.mxcl.mysql@5.7.plist

  ➜  ~ ps aux | grep mysql | grep -v grep | awk '{print $2}' | xargs sudo kill -9

  ➜  ~ /usr/local/opt/mysql@5.7/bin/mysqld_safe --datadir=/usr/local/var/mysql

  ➜  ~ brew services start mysql@5.7

  Service `mysql@5.7` already started, use `brew services restart mysql@5.7` to restart.
  ➜  ~ brew services list
  mysql@5.7               started mac  ~/Library/LaunchAgents/homebrew.mxcl.mysql@5.7.plist

  ➜  ~ mysql -u root -p
  Enter password:
  Welcome to the MySQL monitor.  Commands end with ; or \g.
