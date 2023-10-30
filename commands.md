# Search
**find** \
`find . -name flag1.txt` - find the file named “flag1.txt” in the current directory \
`find /home -name flag1.txt` - find the file names “flag1.txt” in the /home directory \
`find / -type d -name config` - find the directory named config under “/” \
`find / -type f -perm 0777` - find files with the 777 permissions (files readable, writable, and executable by all users) \
`find / -perm a=x` - find executable files \
`find /home -user frank` - find all files for user “frank” under “/home” \
`find / -mtime 10` - find files that were modified in the last 10 days \
`find / -atime 10` - find files that were accessed in the last 10 day \
`find / -cmin -60` - find files changed within the last hour (60 minutes) \
`find / -amin -60` - find files accesses within the last hour (60 minutes) \
`find / -size 50M` - find files with a 50 MB size \

**fd** fd is a better search command line tool than `find`

# Terminal emulators
`tio` - use `/dev/serial/by-id/<device-id>` as device for uniqueness
  `tio -b 115200 -d 8 -s 1 none /dev/serial/by-id/<device-id>`
