# Storage-of-Last-Resort
Ansätze und Techniken für Unveränderliche (Immutable) Backups

## Unveränderliche (Immutable) Backups  
Die Idee ist, dass man einmal schreibt und dann die Dateien (Backups) für eine selbst definierte Zeitspanne geschützt sind. Selbst der Backup-Administrator kann sie nicht löschen, bevor die definierte Zeitspanne verstrichen ist.

### S3 Object Storage 
Der S3 Object Storage bietet die möglichkeit Datenobjecte für definierte Zeiträume wegzusperren.   
WASABI ist z.Z. der günstigste Anbieter auf dem Markt.

### Backup Software
Sinnvoll ist es wenn die Backup Software Immutable Backups unterstützt.
VEEAM bietet hier sinnvolle Möglichkeiten.
Viele Cloud Backup Lösungen bieten diese Möglichkeit an.

### Links
(Strategien zum Schutz von Veeam Backups durch unveränderliche Repository Server mit Linux XFS)[https://www.elasticsky.de/2021/01/strategien-zum-schutz-von-veeam-backups-durch-unveraenderliche-repository-server-mit-linux-xfs/]

### Lösungen
[ceph](https://ceph.io/en/)  
Ceph ist eine Open Source Lösung, die als verteiltes System Block-, Datei- und Objekt-basierten Speicher zur Verfügung stellen kann und die Anforderungen, welche unter dem Begriff Software-defined Storage verstanden werden, erfüllt.

[TrueNAS Core/FreeNas](https://www.truenas.com/truenas-core/)  
TrueNAS (ehemals FreeNAS) ergänzt das eigene LAN um ein Netzwerklaufwerk (Network-Attached-Storage - NAS) zum Speichern von Dateien und Medien.
  
[IONOS Object Speicher](https://cloud.ionos.de/storage/object-storage)  
S3 Object Storage von IONOS Cloud macht Unternehmen den digitalen Wandel leicht. Speichern und verwalten Sie variable Datenmengen besonders flexibel, einfach und kostengünstig. Sie brauchen anpassungsfähigen Speicherplatz für Filesharing, Backups und Archive? Wollen Sie Unternehmensdaten, Medienbibliotheken oder unstrukturierte Rohdaten für Big-Data zuverlässig vorhalten? S3 Object Storage von IONOS Cloud ist Ihre ideale Lösung – auch zur Speicherung geschäftskritischer Daten.
Dank S3 Object Lock erfüllt es alle gesetzlichen Vorgaben für die Daten-Langzeitspeicherung.

[QuObjects QNAP](https://www.qnap.com/de-de/software/quobjects)  
QuObjects wurde für Entwickler von Objektdiensten entwickelt und ermöglicht die Erstellung leistungsfähiger, S3-kompatibler Entwicklungsumgebungen auf einem QNAP NAS. Es ist auch ein idealer Vor-Ort-Speicher für die Sicherung von kalten Daten aus der Cloud, um die Kosten für Cloud-Speicher zu reduzieren.  
