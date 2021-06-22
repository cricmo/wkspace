**mac下 删除启动台的应用图标**

> sqlite3 $(find /private/var/folders \( -name com.apple.dock.launchpad -a -user $USER \) 2> /dev/null)/db/db "DELETE FROM apps WHERE title='应用名称';" && killall Dock



