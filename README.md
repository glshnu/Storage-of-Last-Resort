# Storage-of-Last-Resort
Ansätze und Techniken für Unveränderliche (Immutable) Backups

##Unveränderliche (Immutable) Backups  
Die Idee ist, dass man einmal schreibt und dann die Dateien (Backups) für eine selbst definierte Zeitspanne geschützt sind. Selbst der Backup-Administrator kann sie nicht löschen, bevor die definierte Zeitspanne verstrichen ist.

###S3 Object Storage 
Der S3 Object Storage bietet die möglichkeit Datenobjecte für definierte Zeiträume wegzusperren.   
WASABI ist z.Z. der günstigste Anbieter auf dem Markt.

### Backup Software
Sinnvoll ist es wenn die Backup Software Immutable Backups unterstützt.
VEEAM bietet hier sinnvolle Möglichkeiten.
Viele Cloud Backup Lösungen bieten diese Möglichkeit an.

### Links
(Strategien zum Schutz von Veeam Backups durch unveränderliche Repository Server mit Linux XFS)[https://www.elasticsky.de/2021/01/strategien-zum-schutz-von-veeam-backups-durch-unveraenderliche-repository-server-mit-linux-xfs/]
