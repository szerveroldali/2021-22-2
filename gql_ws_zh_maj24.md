# Szerveroldali webprogramozás - GraphQL, Websocket zárthelyi

_2022. május 24. 15:30-18:45 (3 óra kidolgozás + 15 perc beadás)._

Tartalom:
- [Szerveroldali webprogramozás - GraphQL, Websocket zárthelyi](#szerveroldali-webprogramozás---graphql-websocket-zárthelyi)
  - [Tudnivalók](#tudnivalók)
  - [Hasznos linkek](#hasznos-linkek)
  - [Kezdőcsomag](#kezdőcsomag)
  - [GraphQL (20 pont)](#graphql-20-pont)
    - [Modellek](#modellek)
    - [Típusdefiníció](#típusdefiníció)
    - [1. feladat: `tracks` (1 pont)](#1-feladat-tracks-1-pont)
    - [2. feladat: `track` (1 pont)](#2-feladat-track-1-pont)
    - [3. feladat: `publicNonEmptyPlaylists` (4 pont)](#3-feladat-publicnonemptyplaylists-4-pont)
    - [4. feladat: `myNonEmptyPlaylists` (3 pont)](#4-feladat-mynonemptyplaylists-3-pont)
    - [5. feladat: `myStats` (4 pont)](#5-feladat-mystats-4-pont)
    - [6. feladat: `stats` (7 pont)](#6-feladat-stats-7-pont)
  - [Websocket/Socket.io (10 pont)](#websocketsocketio-10-pont)
    - [1. feladat: `new-game` (2 pont)](#1-feladat-new-game-2-pont)
    - [2. feladat: `tip` (3 pont)](#2-feladat-tip-3-pont)
    - [3. feladat: `end-game` (5 pont)](#3-feladat-end-game-5-pont)

## Tudnivalók

- Kommunikáció
  - **A Teams csoport Általános csatornáján a zárthelyi egész ideje alatt lesz egy meeting! Elsősorban itt válaszolunk a felmerülő kérdésekre, valamint az időközben felmerülő információkat is itt osztjuk meg veletek, ezért erősen ajánlott csatlakozni!**
  - Ha a zárthelyi közben valamilyen problémád/kérdésed adódik, akkor írj nyugodtan a közös meeting chatbe vagy az oktatódnak privát chaten.
  - A közös meeting chaten tilos megosztani megoldásokat / részmegoldásokat!
- Időkeret
  - **A zárthelyi megoldására 3 óra áll rendelkezésre.**
- Beadás
  - **A beadásra az alap időkereten túl további *15* perc áll rendelkezésre. Ez a +15 perc *ténylegesen* a beadásra van! A határidő lejárta után a Canvas lezár, és további beadásra nincs lehetőség!**
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

## Hasznos linkek

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

## Kezdőcsomag

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

## GraphQL (20 pont)

> :warning: A feladatot a kezdőcsomagon belül a `graphql/graphql/typedefs.gql`, `graphql/graphql/resolvers.js` fájlokba kell kidolgozni. 

A GraphQL Playground felület az alábbi linkeken érhető el, ha fut a szerver:
  - http://127.0.0.1:4000/graphql

### Modellek

Az alábbi modelleket készen kapod, ami tartalmazza a következőket: migration, model, seeder. **Tehát nem neked kell őket megírni, neked csak annyi a feladatod, hogy a készen kapott fájlokat bemásolod és inicializálod az adatbázist (`npm run gql:db`), hogy használni tudd!** Az adatokat lokális SQLite adatbázisban kell tárolni.

Modellek:

`User`: felhasználó
- `id`
- `email`: string, unique (az email egyedi), email
- `password`: string, bcrypt hashed
- `name`: string
- `isAdmin`: boolean, default: `false`
- `createdAt`
- `updatedAt`

`Playlist`: lejátszási lista
- `id`
- `title`: string *(lejátszási lista címe)*
- `private`: boolean, default: `false` *(nyilvános-e)*
- `UserId`: integer, references `id` on `Users` *(melyik felhasználóé)*
- `createdAt`
- `updatedAt`

`Track`: zeneszám
- `id`
- `title`: string *(zeneszám címe)*
- `length`: integer *(zeneszám hossza másodpercekben)*
- `author`: string, nullable *(zeneszám szerzője)*
- `genres`: string, nullable *(zeneszám műfajai, egyszerűen szövegként)*
- `album`: string, nullable *(melyik albumba tartozik a szám - csak szövegként)*
- `url`: string *(zeneszámra mutató hivatkozás, pl. Spotify link, stb)*
- `createdAt`
- `updatedAt`

A fenti modellek közötti relációk pedig a következőképpen alakulnak:

- `User` 1-N `Playlist`
- `Playlist` N-N `Track`

### Típusdefiníció

Adott az alábbi GraphQL típusdefiníció. Másold be a kezdőcsomagba, ezt követően pedig implementálod a szükséges műveleteket. A típusdefiníció így teljes, nem kell kiegészítened, csak vedd ki a kommentet (#) az elől, amit implementáltál, hogy a typedefs és a resolvers összhangban maradjon.

```graphql
type Query {
    #tracks: [Track]!
    #track(id: ID!): Track
    #publicNonEmptyPlaylists: [Playlist]!
    #myNonEmptyPlaylists: [Playlist]!
    #myStats: MyStats
    #stats: Stats
}

type User {
    id: ID!
    email: String!
    createdAt: DateTime!
    updatedAt: DateTime!
    # Asszociációk
    #playlists: [Playlist]!
}

type Playlist {
    id: ID!
    title: String!
    private: Boolean!
    createdAt: DateTime!
    updatedAt: DateTime!
    # Számított mezők
    #averageTrackLength: Float!
    # Asszociációk
    #owner: User!
    #tracks: [Track]!
}

type Track {
    id: ID!
    title: String!
    length: Int!
    author: String
    genres: String
    album: String
    url: String!
    createdAt: DateTime!
    updatedAt: DateTime!
}

type MyStats {
    playlistsCount: Int!
    nonEmptyPlaylistsCount: Int!
    uniqueTracksCount: Int!
}

type Stats {
    # Azon felhasználók száma, akiknek van legalább 1 playlistje
    playlistOwnersCount: Int!
    # Azon playlist-ek száma, amelyekhez tartozik legalább 1 track
    nonEmptyPlaylistsCount: Int!
    # 3 percnél hosszabb trackek száma
    longTracksCount: Int!
    # Olyan nemüres playlist-ek (nem üres = van legalább 1 track), amelyekben van legalább 1 hosszú track (vagyis legalább 3 perces)
    nonEmptyPlaylistsWithLongTracksCount: Int!
    # Átlagosan hány track tartozik egy playlist-hez
    averageTracksCount: Float!
    # Átlagosan hány playlist tartozik egy user-hez
    averagePlaylistsCountPerUser: Float!
    # Melyik a legnépszerűbb track, vagyis amelyik a legtöbb playlist-hez hozzá van rendelve (ha több ilyen is van, az első)
    mostPopularTrack: Track
}
```

### 1. feladat: `tracks` (1 pont)
- Összes track lekérése.
- Minta kérés:
  ```graphql
  query {
    tracks {
      id
      title
      length
      author
      genres
      album
      url
      createdAt
      updatedAt
    }
  }
  ```
- Minta válasz:
  ```json
  {
    "data": {
      "tracks": [
        {
          "id": "1",
          "title": "Aut soluta deleniti velit",
          "length": 251,
          "author": "Eduardo Hessel",
          "genres": "Blues",
          "album": "mango",
          "url": "https://szerveroldali-webprog-zenetar.com/20510-aut-soluta-deleniti-velit",
          "createdAt": "2022-05-24T...",
          "updatedAt": "2022-05-24T..."
        },
        {
          "id": "2",
          "title": "Optio odit dolor",
          "length": 256,
          "author": "Chad Mann",
          "genres": "Rock",
          "album": "tunic",
          "url": "https://szerveroldali-webprog-zenetar.com/41043-optio-odit-dolor",
          "createdAt": "2022-05-24T...",
          "updatedAt": "2022-05-24T..."
        },
        STB.
      ]
    }
  }
  ```

### 2. feladat: `track` (1 pont)
- Egy adott track lekérése ID alapján.
- Minta kérés:
  ```graphql
  query {
    track(id: 1) {
      id
      title
      length
      author
      genres
      album
      url
      createdAt
      updatedAt
    }
  }
  ```
- Minta válasz, ha létezik a track:
  ```json
  {
    "data": {
      "track": {
        "id": "1",
        "title": "Aut soluta deleniti velit",
        "length": 251,
        "author": "Eduardo Hessel",
        "genres": "Blues",
        "album": "mango",
        "url": "https://szerveroldali-webprog-zenetar.com/20510-aut-soluta-deleniti-velit",
        "createdAt": "2022-05-24T...",
        "updatedAt": "2022-05-24T..."
      }
    }
  }
  ```
- Minta válasz, ha nem létezik a track:
  ```json
  {
    "data": {
      "track": null
    }
  }
  ```

### 3. feladat: `publicNonEmptyPlaylists` (4 pont)
- Azon playlist-ek lekérése, amelyek nyilvánosak (vagyis a `private` mezőjük `false`) és tartozik hozzájuk legalább egy track.
  - További részfeladatok:
    - A Playlist-hez fel kell venni egy `averageTrackLength` mezőt, ami az adott playlist-hez tartozó track-ek átlagos hosszát adja meg (`length` mező - track hossza másodpercekben).
    - A Playlist-hez létre kell hozni az `owner` és a `tracks` mezőket is, ezekkel kérhető le, hogy melyik felhaszbálóhoz tartozik a playlist, illetve az, hogy konkrétan mely track-ek tartoznak hozzá.
- Minta kérés:
  ```graphql
  query {
    publicNonEmptyPlaylists {
      id
      title
      private
      createdAt
      updatedAt
      averageTrackLength
      owner {
        email
      }
      tracks {
        title
        length
      }
    }
  }
  ```
- Minta válasz:
  ```json
  {
    "data": {
      "publicNonEmptyPlaylists": [
        {
          "id": "1",
          "title": "officia",
          "private": false,
          "createdAt": "2022-05-24T...",
          "updatedAt": "2022-05-24T...",
          "averageTrackLength": 231.75,
          "owner": {
            "email": "user1@szerveroldali.hu"
          },
          "tracks": [
            {
              "title": "Aspernatur modi fugiat voluptatibus dolor sed aut doloribus quis molestiae",
              "length": 200
            },
            {
              "title": "Necessitatibus et aut esse eos fugiat sint cum perferendis",
              "length": 306
            },
            {
              "title": "Et error ut illum architecto id quo at aliquid facere",
              "length": 184
            },
            {
              "title": "Aut eveniet aut fugiat doloremque nesciunt unde iusto earum sed",
              "length": 237
            }
          ]
        },
        STB.
      ]
    }
  }
  ```

### 4. feladat: `myNonEmptyPlaylists` (3 pont)
- Visszaadja a bejelentkezett felhasználó azon playlist-jeit, amelyekhez tartozik legalább egy track.
- Értelemszerűen a végpont hitelesített, hiszen tudni kell, hogy melyik felhasználó playlist-jeit kell lekérni.
- Segítség a hitelesítéshez:
  1. Mivel a felhasználók seedelve lettek és a login implementálva van, ezért a bejelentkezéshez csak küldj egy POST kérést a http://localhost:4000/auth/login végpontra az alábbi request body szerint:
     ```json
     {
       "email": "user1@szerveroldali.hu",
       "password": "password"
     }
     ```
  2. Sikeres bejelentkezés esetén a válaszban visszakapod a szerver által aláírt tokent:
     ```json
     {
       "token": "<TOKEN>",
     }
     ```
  3. A GraphQL Playground bal oldali paneljének az alján található egy "HTTP HEADERS" rész, ahol megadható a token az alábbi minta szerint:
     ```json
     {
       "Authorization": "Bearer <TOKEN>"
     }
     ```
     ![GraphQL Playground hitelesítés](https://i.imgur.com/cuJr757.png)
     - Ha mindent jól csináltál, akkor a kérésed hitelesített lesz.
- Minta kérés:
  ```graphql
  query {
    myNonEmptyPlaylists {
      id
      title
      private
      createdAt
      updatedAt
    }
  }
  ```
- Minta válasz:
  ```json
  {
    "data": {
      "myNonEmptyPlaylists": [
        {
          "id": "5",
          "title": "totam",
          "private": false,
          "createdAt": "2022-05-24T...",
          "updatedAt": "2022-05-24T..."
        },
        STB.
      ]
    }
  }
  ```

### 5. feladat: `myStats` (4 pont)
- Visszaadja a bejelentkezett felhasználóhoz tartozó különféle statisztikákat:
  - `playlistsCount`: hány playlist tartozik a felhasználóhoz
  - `nonEmptyPlaylistsCount` hány nem üres playlist tartozik a felhasználóhoz, vagyis hány olyan lejátszási listája van, amelyikhez tartozik legalább 1 db track
  - `uniqueTracksCount`: hány egyedi track van a felhasználó playlist-jeihez rendelve. Magyarázat:  
    - legyenek T1, T2, T3, T4, T5 trackek, és 
    - a user-nek legyen 2 playlist-je: P1 és P2. 
      - P1-hez tartozzanak a T1, T2, T3 trackek, 
      - P2-höz pedig a T2, T3, T4 track-ek.
    - Ekkor a user-hez tartozó track-ek: T1, T2, T3, T2, T3, T4, azonban ezek még nem egyediek. Mivel a T2 és a T3 is duplán szerepel, ezért azokat csak egyszer kell venni az egyedi track-ekhez, vagyis az egyedi track-ek a következők lesznek: T1, T2, T3, T4. -> Az egyedi track-jeinek a száma jelen esetben 4.
- Minta kérés:
  ```graphql
  query {
    myStats {
      playlistsCount
      nonEmptyPlaylistsCount
      uniqueTracksCount
    }
  }
  ```
- Minta válasz:
  ```json
  {
    "data": {
      "myStats": {
        "playlistsCount": 3,
        "nonEmptyPlaylistsCount": 3,
        "uniqueTracksCount": 18
      }
    }
  }
  ```

### 6. feladat: `stats` (7 pont)
- Visszaad különféle statisztikákat (egyikhez se kell hitelesítés):
  - `playlistOwnersCount`: Azon felhasználók száma, akiknek van legalább 1 playlistje
  - `nonEmptyPlaylistsCount`: Azon playlist-ek száma, amelyekhez tartozik legalább 1 track 
  - `longTracksCount`: 3 percnél hosszabb trackek száma
  - `nonEmptyPlaylistsWithLongTracksCount`: Olyan nemüres playlist-ek (nem üres = van legalább 1 track), amelyekben van legalább 1 hosszú track (vagyis legalább 3 perces)
  - `averageTracksCount`: Átlagosan hány track tartozik egy playlist-hez
  - `averagePlaylistsCountPerUser`: Átlagosan hány playlist tartozik egy user-hez
  - `mostPopularTrack`: Melyik a legnépszerűbb track, vagyis amelyik a legtöbb playlist-hez hozzá van rendelve (ha több ilyen is van, az első)
- Tipp: *Ezek a feladatok megoldhatók "favágó" módszerrel. Ha nem megy, ne vesztegesd az időd egy optimális, elegáns Sequelize kérés megírásával, bőven jó a for ciklus, map, stb egy async fv-ben. Azokhoz elég tényleg csak az alap Sequelize-os műveleteket ismerni :)*
- Minta kérés
  ```graphql
  query {
    stats {
      playlistOwnersCount
      nonEmptyPlaylistsCount
      longTracksCount
      nonEmptyPlaylistsWithLongTracksCount
      averageTracksCount
      averagePlaylistsCountPerUser
      mostPopularTrack {
        id
      }
    }
  }
  ```
- Minta válasz
  ```json
  {
    "data": {
      "stats": {
        "playlistOwnersCount": 3,
        "nonEmptyPlaylistsCount": 7,
        "longTracksCount": 12,
        "nonEmptyPlaylistsWithLongTracksCount": 7,
        "averageTracksCount": 8.857142857142858,
        "averagePlaylistsCountPerUser": 1.75,
        "mostPopularTrack": {
          "id": "3"
        }
      }
    }
  }
  ```

## Websocket/Socket.io (10 pont)

A feladatod egy leegyszerűsített lottójáték elkészítése. A játékot az admin indítja el és az admin is állítja meg jelszóval védett végpontok használatával (`new-game` és `end-game`). Nincs kimondottan "admin" jellegű kliens, az egyszerűség kedvéért tekintsük adminnak azt a teszőleges klienst, aki ismeri a titkos jelszót a végpontokhoz. Tippelni (`tip`) akkor lehet, ha éppen van folyamatban lévő játék (vagyis a `db`-ben lévő `game` property alatt lévő object nem üres), hiszen ha az admin megállítja a játékot, akkor addig nincs folyamatban lévő játék, amíg az admin újat nem indít. Egy kliens akár többször is tippelhet egy játékon belül. Az egyszerűség kedvéért mindössze 15 számból kell eltalálni 5 számot. A játék végén meg kell jeleníteni kétféle statisztikát: minden tippről vissza kell jelezni annak, aki megtippelte (`game-ended`), és globálisan ki kell küldeni egy statiszikát, hogy 0, 1, 2, 3, 4 vagy 5 találatos tippekből mennyi volt (`game-stats`).

Az adatokat a szerver memóriájában kell tárolni, az alábbi minta szerint:
```js
let db = {
    game: {
      // Az előre "kihúzott" nyerő számok:
      numbers: [1,2,3,4,5],
      // A kliensek által megtett tippek (objektumok tömbje):
      tips: [
        { socket: "socket1": numbers: [3,4,5,6,7] }
      ]
    }
};
```

> :warning: A feladatot a kezdőcsomagon belül a `websocket/events.js` fájlba kell kidolgozni.

**Ezekre figyelj, hogy az automata tesztelő működjön:**
- *Az adatokat a `db`-be tárold és onnan is olvasd ki. A fenti példa elnevezéseit és felépítését kövesd, pl. a `numbers` maradjon `numbers`, NE legyen pl. `drawnNumbers`!*
- *A végpontoknak két paramétere legyen, ahogy gyakorlatokon tanultad: `data` és `ack`, ahol a `data` egy objektum, ami tartalmazza az összes bemenő adatot, mivel a tesztelő eszerint fogja hívni a végpontjaidat.*
- *Pontosan kövesd a feladatokban megadott hibaüzeneteket, mivel a tesztelő azt a string-et várja error message-nek, amit a feladatban kérünk.*

A feladatot a kezdőcsomagon belül a `websocket/events.js` fájlba kell kidolgozni.

### 1. feladat: `new-game` (2 pont)
  - Új játék tárolása az adatbázisban, ha éppen nem fut játék (vagyis ha a `db.game` üres objektum). A tárolás a feladat elején adott minta szerint történjen:
    ```js
    db.game = {
      numbers: [ /*Már a játék indításakor kihúzunk 5 db egyedi számot az [1,15] intervallumból. */ ],
      tips: []
    }
    ```
  - Paraméterek:
    - `password`: a titkos admin jelszó, ami elindítja a játékot. Ez szerveroldalon fixen `2444666668888888` legyen *(kimondva 12345678 azaz egy 2, három 4, öt 6, hét 8)*
  - Válasz (acknowledgement):
    - Nem megadott / hibás jelszó esetén: `{ status: 'error', message: 'Invalid password'}`
    - Ha van már folyamatban lévő játék (a `db.game` nem üres objektum): `{ status: 'error', message: 'Game is already in progress'}`
    - Optimális esetben: `{ status: 'ok' }`

### 2. feladat: `tip` (3 pont)
  - Tipp eltárolása az adatbázisban, ha van folyamatban lévő játék és a megadott tipp megfelelő. A `game.tips` tömbbe kell belerakni a kliens által küldött tippet:
    ```js
    { socket: "<Kliens Socket ID>": numbers: [ /* tippelt számok */ ] }
    ``` 
  - Paraméterek
    - `numbers`: a tippelt számok, ami egy 5 elemű, az [1,15] intervallumba eső egyedi számokat tartalmazó tömb
  - Válasz (acknowledgement):
    - Ha nincs folyamatban játék (a `db.game` üres objektum): `{ status: 'error', message: 'No game in progress'}`
    - Ha a `numbers` nem tömb: `{ status: 'error', message: 'Not an array'}`
    - Ha a `numbers` hossza nem 5: `{ status: 'error', message: 'Invalid length'}`
    - Ha valamelyik elem invalid: `{ status: 'error', message: 'X is invalid'}`
      - pl. ha a `numbers` értéke [1,2,3,4,"a"], akkor: `{ status: 'error', message: 'a is invalid'}` (hiszen az "a" nem szám)
      - pl. ha a `numbers` értéke [1,2,33,4,5], akkor: `{ status: 'error', message: '33 is invalid'}` (hiszen a 33 nagyobb, mint 15)
    - Ha a `numbers` nem egyedi számokból áll: `{ status: 'error', message: 'Numbers are not unique!'}`
    - Optimális esetben: `{ status: 'ok' }`

### 3. feladat: `end-game` (5 pont)
  - Játék befejezése, ha van éppen folyamatban lévő játék. Az adatbázisból törölni kell a játék adatait, vagyis az adatbázisban üressé kell tenni a `game` property-hez tartozó object-et:
    ```js
    {
      // A game üres objektum legyen a db-n belül
      game: {}
    }
    ```
  - A játék végén minden kliens (azok is, akik nem vettek részt a játékban, tehát nem tippeltek) kapjon egy `game-stats` üzenetet, ami azt tartalmazza, hogy az egyes találatokból (0 találat, 1 találat, ..., 5 találat) hány db volt. Minta:
    ```json
    { "0": 1, "1": 0, "2": 0, "3": 0, "4": 1, "5": 1 }
    ```
  - A játék végén minden olyan kliens, aki részt vett a játékban (vagyis beküldött legalább egy tippet) tippenként kapjon egy `game-ended` üzenetet, ami az adott tippjére vonatkozó adatokat adja meg. Ennek szerkezete a következő legyen:
    ```js
    {
      // A számok minden esetben növekvő sorrendben jelenjenek meg függetlenül attól, milyen sorrendben lettek eltárolva!
      drawnNumbers: /* Mely számok lettek kihúzva */,
      yourTips: /* A kliens az adott tippben melyik számokat jelölte meg */,
      hits: /* A kliens az adott tippel mely számokat találta el */,
      misses: /* A kliens az adott tippel mely számokat vétette el */,
      youWon: /* A tipp 5 találatos volt-e? */
    }
    ```
    - Minta:
      ```json
      {
        "drawnNumbers": [1,2,3,4,5],
        "yourTips": [3,4,5,6,7],
        "hits": [3,4,5],
        "misses": [1,2],
        "youWon": false
      }
      ```
  - Paraméterek:
    - `password`: a titkos admin jelszó, ami leállítja a játékot. Ez szerveroldalon fixen `2444666668888888` legyen *(kimondva 12345678 azaz egy 2, három 4, öt 6, hét 8)*
  - Válasz (acknowledgement):
    - Nem megadott / hibás jelszó esetén: `{ status: 'error', message: 'Invalid password'}`
    - Ha nincs folyamatban lévő játék (a `db.games` üres objektum): `{ status: 'error', message: 'No game in progress'}`
    - Optimális esetben: `{ status: 'ok' }`
