* crontab -e -u minecraft
* @reboot bash /etc/init.d/multicraft start
* nano /etc/init.d/multicraft

<pre><code>#!/bin/sh

### BEGIN INIT INFO
# Provides:          Multicraft daemon on boot
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Boot Multicraft daemon.
# Description:       Cron task.
### END INIT INFO
MULTICRAFT="/home/minecraft/multicraft"

case "$1" in
    start)
        #Stop command
        $MULTICRAFT/bin/multicraft -v start
    ;;
    stop)
        #Stop command
        $MULTICRAFT/bin/multicraft -v stop
    ;;
    restart)
        $MULTICRAFT/bin/multicraft -v restart
        #Restart command
    ;;
    *)
    echo "Usage: $0 {start|stop|restart}"
    exit 1
    ;;
esac
exit 0
</code></pre> 

* chmod a+x /etc/init.d/multicraft 
* update-rc.d multicraft defaults 
* service multicraft {start|stop|restart}
