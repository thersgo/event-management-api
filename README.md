# Piletirakenduse backend

REST API rakendus, mis kasutab DI, Repository pattern, DTO, valideerimine,
SSO autentimist jpm. Rakendus ehitatakse ülesse ticketite kaupa, kus iga ticket
viib rakenduse järgmisesse staatusesse. Iga ticket sõltub varasemast ning
tehakse järjekorras.

**👉 Alusta siit: [ALUSTA.md](ALUSTA.md)**

## Kasutamine

- `npm install` paigalda teeke
- `npm run start` käivita server

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
