# Piletirakenduse backend

REST API rakendus, mis kasutab DI, Repository pattern, DTO, valideerimine,
SSO autentimist jpm. Rakendus ehitatakse ülesse ticketite kaupa, kus iga ticket
viib rakenduse järgmisesse staatusesse. Iga ticket sõltub varasemast ning
tehakse järjekorras.

**👉 Alusta siit: [ALUSTA.md](ALUSTA.md)**

## Kasutamine

- `npm install` paigalda teeke
- `npm run start` käivita server
- `npm lint` leiab koodist kasutamata muutujad, ohtlikud mustrid ja muud vead
- `npm format` vormindab ja parandab koodistiili ja struktuuri nagu taandus, jutumärgid, reapikkused
- `npm run format:check` vaatab üle, et millised read parandatakse ära kui käivitada format käsk
- `docker compose up -d` alustab docker'i ja sellekaudu postgres'i
- `docker compose ps` loendab docker'i konteinereid ning nende staatused
- `docker compose down` peatab ja eemaldab kõik docker'i konteinereid

## Kaustastruktuur

```
src/
├── event/                 ← üks domeen = üks kaust
│   ├── event.routes.ts        aadressid + ühendused (DI)
│   ├── event.controller.ts    HTTP: valideeri, kutsu service'it, tee vastus
│   ├── event.service.ts       äriloogika
│   ├── event.repository.ts    ainus koht, kus on SQL
│   └── dto/                   päringu ja vastuse kujud
├── shared/                ← mitme domeeni ühine (vead, valideerimine)
├── config/                ← keskkonnamuutujad
├── db/                    ← andmebaasi ühendus ja skeemid
├── scripts/               ← käsurea skriptid (seeder, make-admin)
├── app.ts
└── server.ts
tests/                     ← peegeldab src/ struktuuri
```

## Uuenduste tegemine

| eesliide | tähendus                                     |
| :------- | :------------------------------------------- |
| feat     | uus käitumine                                |
| fix      | vea parandus                                 |
| refactor | koodi ümberkorraldus ilma käitumist muutmata |
| chore    | seadistus, paketid                           |
| docs     | README, dokumentatsioon                      |
| test     | testid                                       |

- loo uue haru
	- nimega `[EESLIIDE]/[ISSUE NUMBER]-[lühike-nimi]`
	- nt: `feat/5-docker-postgres`
- tee muudatused
- `commit -m "[EESLIIDE]: [lühike kirjeldus]"`
	- nt: `"feat: postgres docker composes"`
- pull request
