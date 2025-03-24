# Uzdevumi-par-indeksiem

## Uzdevums 1: Izveidojiet vienīgo indeksu (Unique Index)
Izveidojiet kolekciju ar vienīgu indeksu laukam "email".

db.collection.createIndex({ email: 1 }, { unique: true })
Teorija: Vienīgais indekss nodrošina, ka vērtības konkrētā laukā būs unikālas visās dokumentu kopumā. Tas palīdz izvairīties no dublējumiem.

## Uzdevums 2: Izveidojiet komponētu indeksu (Compound Index)
Izveidojiet indeksu, kas apvieno "firstName" un "lastName" laukus.

db.collection.createIndex({ firstName: 1, lastName: 1 })
Teorija: Komponētie indeksi ļauj veikt efektīvas meklēšanas operācijas vairāku lauku kombinācijām, kas uzlabo pieprasījumu veiktos laikus.

## Uzdevums 3: Veiciet tekstisku meklēšanu (Text Search)
Veiciet meklēšanu dokumentos, kurās ir vārds "MongoDB".

db.collection.find({ $text: { $search: "MongoDB" } })
Teorija: Tekstiskā meklēšana ļauj atrast dokumentus, kas satur noteiktu tekstu jebkurā no indeksētiem laukiem.

## Uzdevums 4: Izveidojiet geogrāfisku indeksu (Geospatial Index)
Izveidojiet indeksu laukam "location", kas satur koordinātes.

db.collection.createIndex({ location: "2dsphere" })
Teorija: Geogrāfiskie indeksi ļauj veikt meklēšanas operācijas ar koordinātēm, piemēram, atrodot punktus noteiktā attālumā no norādītā punkta.

## Uzdevums 5: Veiciet pagriezumu meklēšanu (Wildcard Search)
Izmantojiet wildcards, lai meklētu dokumentus, kuros ir lauki, kas sākas ar "user".

db.collection.find({ "user.*": { $exists: true } })
Teorija: Pagriezuma operatori ļauj veikt meklēšanu visos laukos vai dažādos lauku grupās bez nepieciešamības tos precīzi norādīt.

## Uzdevums 6: Veiciet TTL indeksu (TTL Index)
Izveidojiet TTL indeksu, kas dzēš dokumentus pēc 24 stundām.

db.collection.createIndex({ createdAt: 1 }, { expireAfterSeconds: 86400 })
Teorija: TTL indeksi automātiski dzēš dokumentus pēc noteiktā laika periods, kas ir ideāli logu vai gadījumskatu saglabāšanai.

## Uzdevums 7: Veiciet paralēlu meklēšanu (Parallel Scan)
Meklējiet dokumentus, izmantojot indeksu, bet nevis pilnu kolekcijas skenu.

db.collection.find({ name: "John" }).hint({ name: 1 })
Teorija: Paralēlās meklēšanas metodes optimizē ievades/izejas operācijas, jo tiek izmantots indekss vietā, lai samazinātu datu skaitu, kas tiek apstrādāts.

## Uzdevums 8: Izveidojiet spēcifikācijas indeksu (Sparse Index)
Izveidojiet indeksu, kas nepiekļauj null vērtībām.

db.collection.createIndex({ age: 1 }, { sparse: true })
Teorija: Spēcifikācijas indeksi ignorē dokumentus, kuriem nav vērtības noteiktajā laukā, kas samazina indeksa lielumu un uzlabo efektivitāti.

## Uzdevums 9: Veiciet pagaidu indeksu (Temporary Index)
Izveidojiet indeksu, kas notiek tikai reizi.

db.collection.createIndex({ tempField: 1 }, { expireAfterSeconds: 0 })
Teorija: Pagaidu indeksi tiek izmantoti tikai reizējo operāciju gadījumā un tiek dzēsti pēc tam, kad tās ir pabeigusies.

## Uzdevums 10: Veiciet pagriezuma indeksu (Wildcard Index)
Izveidojiet indeksu, kas ietver visus dokumentus.

db.collection.createIndex({ "$**": 1 })
Teorija: Pagriezuma indeksi ļauj indeksēt visus dokumentu laukus bez nepieciešamības katru no tiem individuāli norādīt.

### Pārbaudes uzdevums 1
Kādu komandu jūs izmantotu, lai dzēstu indeksu no kolekcijas?

db.collection.dropIndex('index');

### Pārbaudes uzdevums 2
Kā jūs varētu veikt meklēšanu pēc dokumentiem, kuru "price" lauks ir lielāks par 100?

db.collection.find({ price: { $gt: 100 } });

### Pārbaudes uzdevums 3
Kā jūs varētu izveidot TTL indeksu, kas dzēstu dokumentus pēc 7 dienām?

db.collection.createIndex({ createdAt: 1 }, { expireAfterSeconds: 604800 })

### Pārbaudes uzdevums 4
Kā jūs varētu veikt meklēšanu, lai atrastu visus dokumentus, kuros "status" ir "active"?

db.collection.find({ status: "active" });

### Pārbaudes uzdevums 5
Kāds ir syntaxs, lai veiktu meklēšanu ar regulāru izteiksmi, piemēram, lai atrastu visus dokumentus, kuru "name" sākas ar "J"?

db.kolekcijas_nosaukums.find({ name: { $regex: "^J" } });
