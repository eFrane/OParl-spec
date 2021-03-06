## Gelöschte Objekte {#geloeschte-objekte}

Wenn ein Objekt gelöscht werden muss (z.B. aufgrund Datenschutz oder Urheberrecht),
so muss das Objekt in OParl gesondert vermerkt werden. Es DARF insbesondere NICHT einfach gelöscht werden,
so dass unter der betreffenden URL ein HTTP Fehlercode 404 oder 410 ausgeliefert wird.

Hintergrund ist, dass alle OParl-Clients zeitnah mitbekommen müssen, wenn ein Objekt gelöscht wurde.
Dies wird durch die folgenden Regeln gewährleistet.

Wenn ein Objekt gelöscht wird, ...

* MUSS das Objekt das zusätzliche Attribut `deleted`: true bekommen
* MUSS das Attribut `modified` auf den Zeitpunkt der Löschung setzen
* MÜSSEN die Attribute `id`, `type` und `created` erhalten bleiben
* MÜSSEN sämtliche anderen Attribute gelöscht werden.

Dies gilt nur für die Hauptobjekte (d.h. System, Body, Organisation, Person, Meeting, Paper, File).
D.h. Subobjekte (LegislativeTerm, Membership, AgendaItem, Consultation) benötigen nicht das
Attribut `deleted`, sondern können einfach gelöscht werden. Beim Löschen einer der Subobjekte
muss allerdings der Wert `modified` des dazugehörigen Hauptobjektes aktualisiert werden.

Dies hat zur Folge, dass das gelöschte Objekt beim Updaten eines Client-Datenbestandes
aktualisiert wird, wenn das normale Update über die in 4.6 angesprochenen Filter erfolgt.
