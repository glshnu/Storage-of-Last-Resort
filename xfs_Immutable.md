Dateisystemattribute geschickt einsetzen
In der IT-Sicherheit ist die Vergabe von Nutzerkonten mit unterschiedlichen Zugriffsrechten unerlässlich. Dadurch wird der Zugriff auf Dateien eingeschränkt und Systemdateien vor den Nutzern eines Systems geschützt. Die Systemadministration ist dann nur als Superuser möglich. Nur dieser hat Zugriff auf alle Dateien des Systems. Gerade bei der Kommandozeilenarbeit unter Linux ist deshalb Vorsicht geboten: ein falsch platzierter Slash oder ein Tippfehler in einem Shellskript und viele wichtige Dateien werden überschrieben oder gelöscht. Auch wird von Angreifern versucht, verschiedene Konfigurationsdateien oder ausführbare Programme zu manipulieren. Um solche Fehler zu verhindern oder zumindest die Konsequenzen einzudämmen, gibt es einige Möglichkeiten. Eine davon ist die Verwendung des Attributes immutable, das für Dateien gesetzt werden kann.

Immutable – Unveränderbar
Das Dateisystemattribut immutable gibt es in den Dateisystemen der ext-Familie, sowie unter anderem bei XFS, ReiserFS und JFS. Dieses und andere Attribute lassen sich nicht, wie die Zugriffsrechte read, write und execute mit dem Befehl chmod setzen, sondern mit chattr. Das chattr-Kommando kann nur vom Superuser benutzt werden.

Eine Datei, die mittels chattr auf immutable gesetzt wird, lässt sich weder löschen noch verändern:

root@server:~# chattr +i beispiel.txt

root@server:~# rm -f beispiel.txt

rm: Entfernen von “beispiel.txt” nicht möglich: Die Operation ist nicht erlaubt

root@server:~# echo “Test” > beispiel.txt

bash: beispiel.txt: Keine Berechtigung

Erst, wenn das Attribut wieder durch den Aufruf von chattr entfernt wurde, kann die Datei bearbeitet werden:

root@server:~# chattr -i beispiel.txt

root@server:~# echo “Test” > beispiel.txt

Hallo

root@server:~# rm -f beispiel.txt

Auf diese Weise lassen sich auch ganze Verzeichnisse, wie z.B. die Konfigurationsdateien in /etc vor versehentlichem Ändern oder Löschen schützen:

root@server:~# chattr -R +i /etc

Mit immutable gegen Angreifer
Bei einem aktuellen, gut abgesicherten Linux-System ist es unwahrscheinlich, dass ein Angreifer Zugriff auf das Superuser-Konto erlangt. Aber für solch einen Fall kann man potentiellen Eindringlingen mit dem immutable-Attribut ein paar Steine in den Weg legen, denn häufig sind sich Angreifer der Existenz des Attributs nicht bewusst, oder es wird nicht von den verwendeten Angriffstools berücksichtigt. Durch das Setzen des immutable-Attributs bei Systemdateien wie z.B. /etc/passwd oder /etc/shadow lässt sich verhindern, dass ein Eindringling neue Benutzer anlegt oder Passwörter ändert. Wird wie oben beschrieben das Verzeichnis /etc auf immutable gesetzt, erschwert dies das Umkonfigurieren des Systems. Setzt man das immutable-Attribut z.B. für die Verzeichnisse /bin, /sbin, /usr/bin usw., kann ein Angreifer die ausführbaren Binärdateien des Systems nicht einfach durch evtl. schadhafte Varianten ersetzen. Hier darf man dann allerdings nicht vergessen, vor einem Softwareupdate das Attribut wieder aufzuheben, da die Updates sonst nicht angewandt werden können. Als zusätzliche Maßnahme kann noch die Verwendung von chattr selbst eingeschränkt werden, indem man das executable-Bit entfernt:

root@server:~# chmod a-x /usr/bin/chattr

Verlassen sollte man sich auf diese zusätzlichen Maßnahmen nicht, denn ein erfahrener, hartnäckiger Angreifer wird irgendwann herausfinden, warum er bestimmte Dateien nicht verändern kann und ihre Attribute zurücksetzen. Idealerweise sollte ein Angreifer erst gar nicht Zugriff auf einen Superuser-Account erlangen. Das immutable-Attribut bietet hier nur einen zusätzlichen Schutz vor automatisierten Angriffen und unerfahrenen Angreifern – und vor versehentlichem Löschen.
