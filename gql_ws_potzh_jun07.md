# Szerveroldali webprogramozás - GraphQL, Websocket pótzárthelyi

_2022. június 07. 15:30-18:45 (3 óra kidolgozás + 15 perc beadás)._

Tartalom:

- [Szerveroldali webprogramozás - GraphQL, Websocket pótzárthelyi](#szerveroldali-webprogramozás---graphql-websocket-pótzárthelyi)
  - [Tudnivalók](#tudnivalók)
  - [Hasznos linkek](#hasznos-linkek)
  - [Kezdőcsomag](#kezdőcsomag)
  - [GraphQL feladatok (15 pont)](#graphql-feladatok-15-pont)
    - [Modellek](#modellek)
    - [Típusdefiníció](#típusdefiníció)
    - [1. feladat: `recipes` (2 pont)](#1-feladat-recipes-2-pont)
    - [2. feladat: `updateIngredient` (2 pont)](#2-feladat-updateingredient-2-pont)
    - [3. feladat: `ingredient` (1 pont)](#3-feladat-ingredient-1-pont)
    - [4. feladat: `smallestStorage` (2 pont)](#4-feladat-smalleststorage-2-pont)
    - [5. feladat: `storeIngredients` (2 pont)](#5-feladat-storeingredients-2-pont)
    - [6. feladat: `changeApplianceName` (3 pont)](#6-feladat-changeappliancename-3-pont)
    - [7. feladat: `statistics` (3 pont)](#7-feladat-statistics-3-pont)
  - [Websocket/Socket.io feladatok (15 pont)](#websocketsocketio-feladatok-15-pont)
    - [1. feladat: `list-rooms` (1 pont)](#1-feladat-list-rooms-1-pont)
    - [2. feladat: `create-room` (2 pont)](#2-feladat-create-room-2-pont)
    - [3. feladat: `join-room` (3 pont)](#3-feladat-join-room-3-pont)
    - [4. feladat: `kick-client` (3 pont)](#4-feladat-kick-client-3-pont)
    - [5. feladat: `ban-client` (3 pont)](#5-feladat-ban-client-3-pont)
    - [5. feladat: `send-message` (3 pont)](#5-feladat-send-message-3-pont)

## Tudnivalók

<details>
<summary>Tudnivalók megjelenítése</summary>

- Kommunikáció
  - **A Teams csoport Általános csatornáján a zárthelyi egész ideje alatt lesz egy meeting! Elsősorban itt válaszolunk a felmerülő kérdésekre, valamint az időközben felmerülő információkat is itt osztjuk meg veletek, ezért erősen ajánlott csatlakozni!**
  - Ha a zárthelyi közben valamilyen problémád/kérdésed adódik, akkor írj nyugodtan a közös meeting chatbe vagy az oktatódnak privát chaten.
  - A közös meeting chaten tilos megosztani megoldásokat / részmegoldásokat!
- Időkeret
  - **A zárthelyi megoldására 3 óra áll rendelkezésre.**
- Beadás
  - **A beadásra az alap időkereten túl további _15_ perc áll rendelkezésre. Ez a +15 perc _ténylegesen_ a beadásra van! A határidő lejárta után a Canvas lezár, és további beadásra nincs lehetőség!**
  - Beadás menete:
    1. Becsomagolás: `npm run zip`
    2. A `zipfiles` mappában létrejött zip fájl ellenőrzése, hogy biztosan minden benne van-e, amit be szeretnél adni.
    3. Az ellenőrzött zip fájl feltöltése ide a Canvas feladathoz.
  - Ha előbb végzel, természetesen a határidő lejártáig bármikor beadhatod a feladatot.
  - A feladatokat `node_modules` mappa nélkül kell becsomagolni egy .zip fájlba, amit a Canvas rendszerbe kell feltölteni!
  - A dolgozat megfelelő és hiánytalan beadása a hallgató felelőssége. Mivel a dolgozat végén külön 15 perces időkeretet adunk a feladat megfelelő, nyugodt körülmények közötti beadására, ezért a határidő lejárta után már nincs lehetőség az elrontott beadások javítására.
- Értékelés
  - A legutoljára beadott megoldás lesz értékelve.
  - **A zárthelyin legalább a pontok 40%-át, vagyis legalább 12 pontot kell elérni**, ez alatt a zárthelyi sikertelen. A GraphQL/Websocket részhez nincs külön-külön minimumpont, a min. 40% a teljes zh 30 pontjára vonatkozik.
  - Vannak részpontok.
  - **A pótzárthelyin nem lehet rontani a zárthelyi eredményéhez képest, csak javítani.** Ez azt jelenti, ha valaki egy adott témakörből (pl. REST API) megírja mindkét zárthelyit (a normált és a pótot is), akkor a jegyébe a kettő közül a jobbik eredményt fogjuk beszámítani. Azonban fontos, hogy ez a "jobbik eredmény" **legalább** 40%, vagyis 12 pont legyen, különben az illető nem teljesítette a tárgyat!
  - **Érvényes nyilatkozat (megfelelően kitöltött statement.txt) hiányában a kapott értékelés érvénytelen, vagyis 0 pont.**
  - Az elrontott, elfelejtett nyilatkozat utólag pótolható: Canvasen kommentben kell odaírni a feladathoz.
- Egyéb
  - A feladatokat Node.js környezetben, JavaScript nyelven kell megoldani, a tantárgy keretein belül tanult technológiák használatával!
  - Ajánlott a Node.js LTS verziójának a használata. Ha a gépedre már telepítve van a Node.js és telepített példány legalább 2 főverzióval le van maradva az aktuálisan letölthető legfrissebbhez képest, akkor érdemes lehet frissíteni.

</details>

## Hasznos linkek

<details>
<summary>Hasznos linkek megjelenítés</summary>

- Dokumentációk
  - Sequelize:
    - [Sequelize dokumentáció](https://sequelize.org/master/)
    - [Model querying basics](https://sequelize.org/master/manual/model-querying-basics.html)
    - [Sequelize asszociációk](https://github.com/szerveroldali/2021-22-1/blob/main/SequelizeAssociations.md) (tantárgyi leírás)
  - GraphQL:
    - [GraphQL dokumentáció](https://graphql.org/learn/)
    - [GraphQL scalars](https://www.graphql-scalars.dev/docs) (a kezdőcsomag tartalmazza)
  - Socket.IO:
    - [Socket.IO dokumentáció](https://socket.io/docs)
    - [Socket.IO szobák működése](https://socket.io/docs/v4/rooms/)
    - [Socket.IO emit cheatsheet](https://socket.io/docs/v4/emit-cheatsheet/)
- Eszközök:
  - [Postman](https://www.postman.com/)
  - [Firecamp Chrome kiegészítő](https://chrome.google.com/webstore/detail/firecamp-a-campsite-for-d/eajaahbjpnhghjcdaclbkeamlkepinbl)
  - [DB Browser for SQLite](https://sqlitebrowser.org/)
- Gyakorlati anyagok:
  - [Tavalyi ZH mintamegoldása](https://github.com/szerveroldali/2021-22-1/tree/main/graphql_websocket_minta)
  - [GraphQL gyakorlati anyag](https://github.com/szerveroldali/2021-22-1/tree/main/esti_3_4_csut_19_30/restapi/graphql)
  - [Socket.IO gyakorlati anyag](https://github.com/szerveroldali/2021-22-1/tree/main/esti_3_4_csut_19_30/websocket)

</details>

## Kezdőcsomag

<details>
<summary>Kezdőcsomag információk megjelenítése</summary>

Segítségképpen biztosítunk egy kezdőcsomagot a zárthelyihez. Csak telepíteni kell a csomagokat, és kezdheted is a fejlesztést.

- A kezdőcsomag elérhető ebben a GitHub repository-ban:
  - https://github.com/szerveroldali/graphql_websocket_kezdocsomag
  - Vagy: [Közvetlen letöltési link](https://github.com/szerveroldali/graphql_websocket_kezdocsomag/archive/refs/heads/main.zip) (zip fájl)
- Az alábbi parancsok érhetők el a kezdőcsomagon belül:
  - GraphQL:
    - `npm run gql:db`: Migrációk és a seeder futtatása nulláról (tiszta adatbázis)
    - `npm run gql:dev`: GraphQL szerver futtatása (fejlesztői)
    - `npm run gql:test`: Automata tesztelő futtatása a GraphQL feladat összes részfeladatára
    - `npm run gql:test 1 2`: Automata tesztelő futtatása a GraphQL feladat konkrét részfeladataira a feladatok sorszáma alapján (pl. itt az 1. és a 2. feladatra)
  - Websocket:
    - `npm run ws:dev`: Websocket (Socket.IO) szerver futtatása (fejlesztői)
    - `npm run ws:test`: Automata tesztelő futtatása a Websocket feladat összes részfeladatára
    - `npm run ws:test 1 2`: Automata tesztelő futtatása a Websocket feladat konkrét részfeladataira a feladatok sorszáma alapján (pl. itt az 1. és a 2. feladatra)
  - `npm run zip`: ZH becsomagolása (automatikus nyilatkozat ellenőrzéssel és kitöltéssel)
  - `npm run prettier`: A projektben lévő összes `.js`, `.json` és `.graphql` fájl formázása Prettier-el

</details>

## GraphQL feladatok (15 pont)

> :warning: A feladatot a kezdőcsomagon belül a `graphql/graphql/typedefs.gql`, `graphql/graphql/resolvers.js` fájlokba kell kidolgozni.

A GraphQL Playground felület az alábbi linkeken érhető el, ha fut a szerver:

- http://127.0.0.1:4000/graphql

### Modellek

Az alábbi modelleket készen kapod, ami tartalmazza a következőket: migration, model, seeder. **Tehát nem neked kell őket megírni, neked csak annyi a feladatod, hogy a készen kapott fájlokat bemásolod és inicializálod az adatbázist (`npm run gql:db`), hogy használni tudd!** Az adatokat lokális SQLite adatbázisban kell tárolni.

Modellek:

- `Storage`: tárolók
  - `id`: integer, auto increment, primary key
  - `name`: string, unique (ugyanaz a név nem szerepelhet kétszer)
  - `capacity`: integer
  - `createdAt`: date
  - `updatedAt`: date
- `Appliance`: konyhai berendezések
  - `id`: integer, auto increment, primary key
  - `name`: string
  - `createdAt`: date
  - `updatedAt`: date
- `Ingredient`: hozzávalók
  - `id`: integer, auto increment, primary key
  - `name`: string
  - `amount`: integer, default value is 0
  - `StorageId`: integer, references `id` on `Storages` _(melyik tárolóhoz tartozik)_
  - `createdAt`: date
  - `updatedAt`: date
- `Recipe`: receptek
  - `id`: integer, auto increment, primary key
  - `name`: string, unique (ugyanaz a név nem szerepelhet egyszerre több beszállítónál)
  - `isVegetarian`: boolean, default value is false
  - `doneCount`: integer, default value is 0 _(hányszor készítették már el a receptet)_
  - `ApplianceId`: integer, references `id` on `Appliances`
  - `createdAt`: date
  - `updatedAt`: date

A fenti modellek közötti relációk pedig a következőképpen alakulnak:

- `Recipe` N - N `Ingredient`
- `Appliance` 1 - N `Recipe`
- `Storage` 1 - N `Ingredient`

### Típusdefiníció

Adott az alábbi GraphQL típusdefiníció. Másold be a kezdőcsomagba, ezt követően pedig implementálod a szükséges műveleteket. A típusdefiníció így teljes, nem kell kiegészítened, csak vedd ki a kommentet (#) az elől, amit implementáltál, hogy a typedefs és a resolvers összhangban maradjon.

```graphql
type Recipe {
  id: ID!
  name: String!
  isVegetarian: Boolean!
  doneCount: Int!
  appliance: Appliance!
  #ingredients: [Ingredient]
  createdAt: DateTime!
  updatedAt: DateTime!
}

input IngredientInput {
  name: String!
  # Default 0
  amount: Int
}

type Ingredient {
  id: ID!
  name: String!
  amount: Int!
  #isInBigStorage: Boolean
  createdAt: DateTime!
  updatedAt: DateTime!
}

type Appliance {
  id: ID!
  name: String!
  createdAt: DateTime!
  updatedAt: DateTime!
}

type Storage {
  id: ID!
  name: String!
  capacity: Int!
  #ingredients: [Ingredient]
  createdAt: DateTime!
  updatedAt: DateTime!
}

type Statistics {
  popularVegetarianRecipeCount: Int
  mostPopularRecipeName: String
  leastPopularRecipeName: String
  bigStoragesCount: Int
  averageDoneCount: Int
}

type Query {
  #recipes: [Recipe]
  #ingredient(id: ID!): Ingredient
  #smallestStorage: Storage
  #statistics: Statistics
}

type Mutation {
  #updateIngredient(ingredientId: ID!, input: IngredientInput): Ingredient
  #storeIngredients(storageId: ID!, ingredients: [IngredientInput]): [Ingredient]
  #changeApplianceName(applianceId: ID!, newName: String): Appliance
}
```

### 1. feladat: `recipes` (2 pont)

- Összes recept lekérése, a hozzá tartozó berendezéssel és hozzávalókkal együtt
  - Kérés:
    ```graphql
    query {
      recipes {
        id
        name
        isVegetarian
        doneCount
        createdAt
        updatedAt
        appliance {
          id
          name
        }
        ingredients {
          id
          name
          amount
        }
      }
    }
    ```
  - Válasz: a recepthez kapcsolt berendezést és hozzávalókat listázni kell a példán látható módon
    ```json
    {
      "data": {
        "recipes": [
          {
            "id": "1",
            "name": "gdxhzzmtzidhaawtoqgwsnzf",
            "isVegetarian": false,
            "doneCount": 40,
            "createdAt": "2022-06-07T...",
            "updatedAt": "2022-06-07T...",
            "appliance": {
              "id": "1",
              "name": "qimowoxbrhahrktghtnqmvqf"
            },
            "ingredients": [
              {
                "id": "1",
                "name": "zlhptyqmeoamewebvkmfpmug",
                "amount": 83
              },
              {
                "id": "2",
                "name": "djtqbxbzeilejbtebglgljzt",
                "amount": 91
              },
              STB.
            ]
          },
          {
            "id": "2",
            "name": "iwxadroljehbzwjrroyfcigi",
            "isVegetarian": false,
            STB.
          }
        ]
      }
    }
    ```

### 2. feladat: `updateIngredient` (2 pont)

- `updateIngredient(ingredientId, input)`
- Egy hozzávaló módosítása. Itt az input azokra a kulcs-érték párosokra utal, amit módosítani szeretnénk.
  - Kérés
    ```graphql
    mutation {
      updateIngredient(ingredientId: 1, input: { name: "UJ_NEV" }) {
        id
        name
        updatedAt
      }
    }
    ```
  - Válasz
    ```json
    {
      "data": {
        "updateIngredient": {
          "id": "1",
          "name": "UJ_NEV",
          "updatedAt": "2022-06-07T..."
        }
      }
    }
    ```

### 3. feladat: `ingredient` (1 pont)

- `ingredient(id)`
- Egy hozzávaló lekérdezése (erre még nem jár pont). Implementáld a `isInBigStorage` mezőt, ami visszaadja, hogy a hozzá tartozó tároló kapacitása nagyobb-e **30**-nál.
  - Kérés:
    ```graphql
    query {
      ingredient(id: 1) {
        id
        name
        isInBigStorage
      }
    }
    ```
  - Válasz:
    ```json
    {
      "data": {
        "ingredient": {
          "id": "1",
          "name": "UJ_NEV",
          "isInBigStorage": true
        }
      }
    }
    ```

### 4. feladat: `smallestStorage` (2 pont)

- Visszaadja az adatbázisban tárolt legkisebb kapacitású tárolót és az összes olyan hozzávalót, amivel ebben található (tehát amikkel relációban van).
  - Kérés:
    ```graphql
    query {
      smallestStorage {
        id
        name
        capacity
        ingredients {
          id
          name
          amount
        }
      }
    }
    ```
  - Válasz:
    ```json
    {
      "data": {
        "smallestStorage": {
          "id": "9",
          "name": "quod",
          "capacity": 2,
          "ingredients": [
            {
              "id": "8",
              "name": "est",
              "amount": 54
            },
            {
              "id": "9",
              "name": "omnis",
              "amount": 80
            }
          ]
        }
      }
    }
    ```

### 5. feladat: `storeIngredients` (2 pont)

- `storeIngredients(storageId, ingredients)`
- Egy megadott tárolóhoz rendel hozzá plusz hozzávalókat. Fontos, hogy az `ingredients` mezőben a hozzávalók mezői vannak (`name`, `amount`) és nem cserélik le a tárolóban lévőeket, hanem kiegészítik azokat (tehát csak hozzáadódnak a tárolóhoz).
  - Kérés:
    ```graphql
    mutation {
      storeIngredients(
        storageId: 4
        ingredients: [
          { name: "ingredient1" }
          { name: "ingredient2", amount: 3 }
        ]
      ) {
        id
        name
        amount
      }
    }
    ```
  - Válasz: A tárolóban lévő hozzávalók.
    ```json
    {
      "data": {
        "storeIngredients": [
          {
            "id": "8",
            "name": "occaecati",
            "amount": 44
          },
          {
            "id": "24",
            "name": "ingredient1",
            "amount": 0
          },
          {
            "id": "25",
            "name": "ingredient2",
            "amount": 3
          }
        ]
      }
    }
    ```

### 6. feladat: `changeApplianceName` (3 pont)

- `changeApplianceName(applianceId, newName)`
- Az `applianceId` mezőben megadott id-jú berendezés nevét lecseréli a `newName` mező értékére, **DE** csak akkor, ha a berendezéshez a receptek kevesebb mint 30%-a tartozik.
  Tehát:

  - ha `BERENDEZÉSHEZ_TARTOZÓ_RECEPTEK_SZÁMA < ÖSSZES_RECEPT_30_SZÁZALÉKA`, akkor megváltozik a neve
  - ha `BERENDEZÉSHEZ_TARTOZÓ_RECEPTEK_SZÁMA >= ÖSSZES_RECEPT_30_SZÁZALÉKA`, akkor nem történik semmi

  - Kérés

    ```graphql
    mutation {
      changeApplianceName(applianceId: 1, newName: "MEGVALTOZOTT") {
        id
        name
      }
    }
    ```

  - Válasz
    ```json
    {
      "data": {
        "changeApplianceName": {
          "id": "1",
          "name": "MEGVALTOZOTT"
        }
      }
    }
    ```

### 7. feladat: `statistics` (3 pont)

- A receptekről készít statisztikát.
  - Kérés:
    ```graphql
    query {
      statistics {
        popularVegetarianRecipeCount
        mostPopularRecipeName
        leastPopularRecipeName
        bigStoragesCount
        averageDoneCount
      }
    }
    ```
  - Válasz: le kell kérni a receptekhez aktuálisan tartozó statisztikákat. A statisztika a következő mezőkből áll:
    - `popularVegetarianRecipeCount`: hány olyan vegetáriánus recept van (`isVegetarian`) amit több mint 10 ember csinált meg (`doneCount`)
    - `mostPopularRecipeName`: annak a receptnek a neve (`name`), aminek a legmagasabb a `doneCount`-ja. Ha több, doneCount-ú recept van, akkor a legkisebb id-jút kell visszaadni
    - `leastPopularRecipeName`: annak a receptnek a neve (`name`), aminek a legalacsonyabb a `doneCount`-ja. Ha több, doneCount-ú recept van, akkor a legkisebb id-jút kell visszaadni
    - `bigStoragesCount`: azon tárolók száma, amelyeknek a kapacitása nagyobb 30-nál
    - `averageDoneCount`: az összes recept `doneCount` mezőjéből vett átlag (lefelé kerekítve, egész számra)
      Az alább példa szerint kell visszaadni a statisztikát:
  - Megjegyzés: Ehhez már új típust is létre kell hozni
    ```json
    {
      "data": {
        "statistics": {
          "popularVegetarianRecipeCount": 8,
          "mostPopularRecipeName": "ut",
          "leastPopularRecipeName": "ipsum",
          "bigStoragesCount": 30,
          "averageDoneCount": 60
        }
      }
    }
    ```

## Websocket/Socket.io feladatok (15 pont)

A feladatod egy chat elkészítése. A klienseknek legyen lehetősége belépni chatszobákba, ahol üzenetet tudnak küldeni a többi tagnak. Egy kliens saját szobát is csinálhat, ahová más kliensek csatlakozhatnak. Ha valaki létrehoz egy szobát, automatikusan a saját szobája adminjává válik, és jogában áll lenémítani tagokat, így ők onnantól kezdve nem írhatnak a többieknek abban a szobában.

Az adatokat a szerver memóriájában kell tárolni, az alábbi minta szerint:

```js
let db = {
  rooms: {
    room1: {
      admin: "socket1",
      members: ["socket1", "socket2", "socket3"],
      bans: [
        {
          socketId: "socket4",
          reason: "No reason",
        },
      ],
      muted: ["socket2"],
      messages: [
        { timestamp: 123456789, client: "socket1", message: "sziasztok" },
        { timestamp: 123456789, client: "socket3", message: "hali" },
      ],
    },
    "Másik szoba": {
      admin: "socket2",
      members: ["socket2"],
      bans: [],
      muted: [],
      messages: [
        { timestamp: 123456789, client: "socket2", message: "foreveralone" },
      ],
    },
  },
};
```

> :warning: A feladatot a kezdőcsomagon belül a `websocket/events.js` fájlba kell kidolgozni.

**Ezekre figyelj, hogy az automata tesztelő működjön:**

- _Az adatokat a `db`-be tárold és onnan is olvasd ki. A fenti példa elnevezéseit és felépítését kövesd!_
- _A végpontoknak két paramétere legyen, ahogy gyakorlatokon tanultad: `data` és `ack` (ahol a `data` egy objektum, ami tartalmazza az összes bemenő adatot), mivel a tesztelő eszerint fogja hívni a végpontjaidat._
- _Pontosan kövesd a feladatokban megadott hibaüzeneteket, mivel a tesztelő azt a string-et várja error message-nek, amit a feladatban kérünk._

### 1. feladat: `list-rooms` (1 pont)

- Elérhető chat szobák listázása
- Paraméterek: -
- Válasz (acknowledgement):
  - Jó esetben: `{ status: 'ok', rooms: ['room1', 'room2', ...] }`
  - Hiba esetén: `{ status: 'error', message: '<hibaüzenet>'}`

### 2. feladat: `create-room` (2 pont)

- Szoba létrehozása. Ilyenkor aki létrehozza a szobát, automatikusan csatlakozik hozzá, illetve az adminjává is válik. A kliens csatlakozását és admin jogát az adatbázisban le kell tárolni, továbbá SocketIO szinten is hozzá kell őt adni a szobához.
- Paraméterek
  - `room`: a létrehozandó szoba neve
- Válasz (acknowledgement):
  - Jó esetben: `{ status: 'ok' }`
  - Hiba esetén:
    - Hiányzó, rossz paraméter: `{ status: 'error', message: '<hibaüzenet>'}`
    - A megadott névvel már létezik szoba: `{ status: 'error', message: 'This name is already taken!'}`

### 3. feladat: `join-room` (3 pont)

- Csatlakozás egy chatszobához. A kliens csatlakozását az adatbázisban is le kell tárolni, továbbá SocketIO szinten is hozzá kell őt adni a szobához.
- Paraméterek
  - `room`: a szoba neve, amihez csatlakozni szeretnénk
- Válasz (acknowledgement):
  - Jó esetben: `{ status: 'ok' }`
  - Hiba esetén:
    - Hiányzó, rossz paraméter: `{ status: 'error', message: '<hibaüzenet>'}`
    - Nem létező szoba: `{ status: 'error', message: 'No such room in our system!'}`
    - A kliens már a szoba tagja: `{ status: 'error', message: 'You are already subscribed to this room!'}`
    - Ha a kliens ki van tiltva a szobából: `{ status: 'error', message: 'You are banned from this room! Reason: <INDOK>'}`
      - az `<INDOK>` helyére a konkrét indok kerüljön, pl. `{ status: 'error', message: 'You are banned from this room! Reason: flood'`

### 4. feladat: `kick-client` (3 pont)

- Az admin ki tud rúgni a szobájából egy klienst.
- Paraméterek
  - `room`: a szoba neve, amelyből ki szeretnénk rúgni a klienst
  - `clientId`: a kirúgandó kliens SocketIO azonosítója
  - `reason`: a kirúgás oka (opcionális)
- Válasz (acknowledgement):
  - Jó esetben:
    - `{ status: 'ok' }`
    - Továbbá a kirúgott kliensnek el kell küldeni a `kicked` üzenetet, a következő adatokkal (minta):
      - `{ room: 'room1', admin: 'socket1', reason: 'káromkodtál' }`
      - Ha nem volt `reason` megadva, az értéke legyen `"Nincs indok"`
  - Hiba esetén:
    - Hiányzó, rossz paraméter: `{ status: 'error', message: '<hibaüzenet>'}`
    - Nem létező szoba: `{ status: 'error', message: 'No such room in our system!'}`
    - A kliens nem a szoba tagja: `{ status: 'error', message: 'You are not subscribed to this room!'}`
    - A kliens nem admin a szobában: `{ status: 'error', message: 'You have no power here, Gandalf the Grey!'}`
    - A kliens saját magát akarja kirúgni: `{ status: 'error', message: 'You can't kick yourself!'}`
    - A célpont nem tagja a szobának: `{ status: 'error', message: 'The target is not a member of the room!'}`

### 5. feladat: `ban-client` (3 pont)

- Az admin ki tud tiltani a szobájából egy klienst. A `kick-client` feladathoz képest itt az a különbség, hogy a kliens nem tud ismét csatlakozni a szobához.
- Paraméterek
  - `room`: a szoba neve, amelyből ki szeretnénk tiltani a klienst
  - `clientId`: a kitiltandó kliens SocketIO azonosítója
  - `reason`: a kitiltás oka (opcionális)
- Válasz (acknowledgement):
  - Jó esetben:
    - `{ status: 'ok' }`
    - Továbbá a kitiltott kliensnek el kell küldeni a `banned` üzenetet, a következő adatokkal (minta):
      - `{ room: 'room1', admin: 'socket1', reason: 'káromkodtál' }`
      - Ha nem volt `reason` megadva, az értéke legyen `"Nincs indok"`
  - Hiba esetén:
    - Hiányzó, rossz paraméter: `{ status: 'error', message: '<hibaüzenet>'}`
    - Nem létező szoba: `{ status: 'error', message: 'No such room in our system!'}`
    - A kliens nem a szoba tagja: `{ status: 'error', message: 'You are not subscribed to this room!'}`
    - A kliens nem admin a szobában: `{ status: 'error', message: 'You have no power here, Gandalf the Grey!'}`
    - A kliens saját magát akarja kitiltani: `{ status: 'error', message: 'You can't ban yourself!'}`
    - A célpont nem tagja a szobának: `{ status: 'error', message: 'The target is not a member of the room!'}`

### 5. feladat: `send-message` (3 pont)

- Üzenet küldése a chat szoba tagjainak, ha nem vagyunk némítva.
- Paraméterek
  - `room`: a szoba neve, amelyben üzenni szeretnénk
  - `message`: üzenet tartalma
- Válasz (acknowledgement):
  - Jó esetben:
    - `{ status: 'ok' }`
    - Továbbá a szobában lévő összes kliensnél (de csak náluk) `message-received` eseményt kell kiváltani, a következő adatokkal (minta):
      - `{ room: 'room1', timestamp: 123456789, client: 'socket1', message: 'sziasztok' }`
  - Hiba esetén:
    - Hiányzó, rossz paraméter: `{ status: 'error', message: '<hibaüzenet>'}`
    - Nem létező szoba: `{ status: 'error', message: 'No such room in our system!'}`
    - A kliens nem a szoba tagja: `{ status: 'error', message: 'You are not subscribed to this room!'}`
    - A kliens némítva van: `{ status: 'error', message: 'You are muted!'}`
