# Szerveroldali webprogramozás - REST API pótzárthelyi

_2022. május 31. 15:30-18:45 (3 óra kidolgozás + 15 perc beadás)_

Tartalom:

- [Szerveroldali webprogramozás - REST API pótzárthelyi](#szerveroldali-webprogramozás---rest-api-pótzárthelyi)
  - [Tudnivalók](#tudnivalók)
  - [Hasznos linkek](#hasznos-linkek)
  - [Kezdőcsomag](#kezdőcsomag)
  - [Feladatok](#feladatok)
    - [`Modellek és relációk`](#modellek-és-relációk)
    - [`1. feladat: Seeder (3 pont)`](#1-feladat-seeder-3-pont)
    - [`2. feladat: GET /free-articles (1 pont)`](#2-feladat-get-free-articles-1-pont)
    - [`3. feladat: GET /articles (3 pont)`](#3-feladat-get-articles-3-pont)
    - [`4. feladat: GET /articles/:id (6 pont)`](#4-feladat-get-articlesid-6-pont)
    - [`5. feladat: PATCH /articles/:id (3 pont)`](#5-feladat-patch-articlesid-3-pont)
    - [`6. feladat: DELETE /articles/:id/delete-comments (3 pont)`](#6-feladat-delete-articlesiddelete-comments-3-pont)
    - [`7. feladat: POST /articles/:id/comment (3 pont)`](#7-feladat-post-articlesidcomment-3-pont)
    - [`8. feladat: POST /set-muted (2 pont)`](#8-feladat-post-set-muted-2-pont)
    - [`9. feladat: GET /stats (6 pont)`](#9-feladat-get-stats-6-pont)

## Tudnivalók

<details>
<summary>Tudnivalók megjelenítése</summary>

- Kommunikáció
  - **A Teams csoport Általános csatornáján a zárthelyi egész ideje alatt lesz egy meeting! Elsősorban itt válaszolunk a felmerülő kérdésekre, valamint az időközben felmerülő információkat is itt osztjuk meg veletek, ezért erősen ajánlott csatlakozni!**
  - Ha a zárthelyi közben valamilyen problémád/kérdésed adódik, akkor írj nyugodtan a közös meeting chatbe vagy az oktatódnak privát chaten.
  - A közös meeting chaten tilos megosztani megoldásokat / részmegoldásokat!
- Időkeret
  - **A zárthelyi megoldására 2 óra áll rendelkezésre.**
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
  - **A zárthelyin legalább a pontok 40%-át, vagyis legalább 12 pontot kell elérni**, ez alatt a zárthelyi sikertelen.
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
    - [Sequelize asszociációk](https://github.com/szerveroldali/leirasok/blob/main/SequelizeAsszociaciok.md) (tantárgyi leírás)
  - Express:
    - [ExpressJS 4 dokumentáció](https://expressjs.com/en/4x/api.html)
- Eszközök:
  - [Postman](https://www.postman.com/)
  - [Firecamp Chrome kiegészítő](https://chrome.google.com/webstore/detail/firecamp-a-campsite-for-d/eajaahbjpnhghjcdaclbkeamlkepinbl)
  - [DB Browser for SQLite](https://sqlitebrowser.org/)

</details>

## Kezdőcsomag

<details>
<summary>Kezdőcsomag információk megjelenítése</summary>

Segítségképpen biztosítunk egy kezdőcsomagot a zárthelyihez. Csak telepíteni kell a csomagokat, és kezdheted is a fejlesztést.

- A kezdőcsomag elérhető ebben a GitHub repository-ban:
  - https://github.com/szerveroldali/restapi_kezdocsomag
  - Vagy: [Közvetlen letöltési link](https://github.com/szerveroldali/restapi_kezdocsomag/archive/refs/heads/main.zip) (zip fájl)
- Automatikus tesztelő: `npm run test <FELADATOK SZÁMAI>`
  - Pl. 1. és 2. feladat tesztelése: `npm run test 1 2`
  - Minden feladat tesztelése: `npm run test`
- Zippelő: `npm run zip`

</details>

## Feladatok

Készíts egy REST API-t Node.js-ben, Express, Sequelize és SQLite3 segítségével, amelyben az alább részletezett feladatokat valósítod meg! A szerver a 4000-es porton fusson!

### `Modellek és relációk`

> :warning: **A modelleket ezen a zárthelyin készen kapod, csak be kell másolnod őket.**

A modellek az alábbiak:

- `User`: újságíró/felhasználó
  - `id`: integer, auto increment, primary key
  - `email`: string, unique, email
  - `password`: string, bcrypt hashed
  - `name`: string
  - `isJournalist`: boolean, default: `false` (újságíró-e)
  - `isPremium`: boolean, default: `false` (prémium tag-e)
  - `isMuted`: boolean, default: `false` (némított-e, azaz írhat-e hozzászólást)
  - `createdAt`: date
  - `updatedAt`: date
- `Article`: cikk
  - `id`: integer, auto increment, primary key
  - `title`: string (a cikk címe)
  - `text`: text, min length: 128 character (a cikk tartalma)
  - `premiumRequired`: boolean, default: `false` (előfizetéshez, azaz prémium tagsághoz kötött-e a cikk)
  - `freeOnFirstDay`: boolean, default: `false` (ha a cikk prémium tagsághoz kötött, első nap ingyenesen elolvasható-e)
  - `commentsEnabled`: boolean, default: `true` (lehetőség van-e hozzászólást írni a cikkhez)
  - `createdAt`: date
  - `updatedAt`: date
- `Comment`: hozzászólás
  - `id`: integer, auto increment, primary key
  - `text`: text (a hozzászólás szövege)
  - `ArticleId`: integer, references `id` on `Articles` (melyik cikk alá írták a kommentet)
  - `UserId`: integer, references `id` on `Users` (ki írta a kommentet)
  - `createdAt`: date
  - `updatedAt`: date

A fenti modellek közötti relációk pedig a következőképpen alakulnak:

- `User` N-N `Article`: Egy újságíró akármennyi cikk szerzője lehet, és egy cikknek is akármennyi újságíró lehet a szerzője
- `User` 1-N `Comment`: Egy felhasználónak akármennyi hozzászólása lehet
- `Article` 1-N `Comment`: Egy cikknek akármennyi hozzászólása lehet

Segítség a relációkkal kapcsolatos műveletekhez:

<details>
<summary>Relációkhoz tartozó metódusok megjelenítése</summary>

- `User`:
  - Cikkek:
    - `get`: User.getArticles(...)
    - `set`: User.setArticles(...)
    - `addMultiple`: User.addArticles(...)
    - `add`: User.addArticle(...)
    - `create`: User.createArticle(...)
    - `remove`: User.removeArticle(...)
    - `removeMultiple`: User.removeArticles(...)
    - `hasSingle`: User.hasArticle(...)
    - `hasAll`: User.hasArticles(...)
    - `count`: User.countArticles(...)
  - Hozzászólások:
    - `get`: User.getComments(...)
    - `set`: User.setComments(...)
    - `addMultiple`: User.addComments(...)
    - `add`: User.addComment(...)
    - `create`: User.createComment(...)
    - `remove`: User.removeComment(...)
    - `removeMultiple`: User.removeComments(...)
    - `hasSingle`: User.hasComment(...)
    - `hasAll`: User.hasComments(...)
    - `count`: User.countComments(...)
- `Article`:
  - Szerzők:
    - `get`: Article.getAuthors(...)
    - `set`: Article.setAuthors(...)
    - `addMultiple`: Article.addAuthors(...)
    - `add`: Article.addAuthor(...)
    - `create`: Article.createAuthor(...)
    - `remove`: Article.removeAuthor(...)
    - `removeMultiple`: Article.removeAuthors(...)
    - `hasSingle`: Article.hasAuthor(...)
    - `hasAll`: Article.hasAuthors(...)
    - `count`: Article.countAuthors(...)
  - Hozzászólások:
    - `get`: Article.getComments(...)
    - `set`: Article.setComments(...)
    - `addMultiple`: Article.addComments(...)
    - `add`: Article.addComment(...)
    - `create`: Article.createComment(...)
    - `remove`: Article.removeComment(...)
    - `removeMultiple`: Article.removeComments(...)
    - `hasSingle`: Article.hasComment(...)
    - `hasAll`: Article.hasComments(...)
    - `count`: Article.countComments(...)
- `Comment`:
  - Cikk:
    - `get`: Comment.getArticle(...)
    - `set`: Comment.setArticle(...)
    - `create`: Comment.createArticle(...)
  - Szerző:
    - `get`: Comment.getAuthor(...)
    - `set`: Comment.setAuthor(...)
    - `create`: Comment.createAuthor(...)

</details>

### `1. feladat: Seeder (3 pont)`

Hozz létre egy seedert, melynek segítségével feltölthető az adatbázis mintaadatokkal! A seeder minél több esetet fedjen le! A megoldás akkor számít teljes értékűnek, ha a seeder minden lehetséges esethez készít néhány adatot, és a relációkat is figyelembe veszi. A seedert az automata tesztelő nem értékeli, a gyakorlatvezető fogja kézzel javítani.

### `2. feladat: GET /free-articles (1 pont)`

Lekéri az összes ingyenes cikket, vagyis azokat, amelyeknek az elolvasása egyáltalán nincs prémium tagsághoz kötve. Mivel ez egy bemelegítő feladat, így itt még elég csak az `Article` `premiumRequired` mezőjét figyelembe venni.

- Minta kérés: `GET http://localhost:4000/free-articles`
- Válasz megfelelő kérés esetén: `200 OK`
  ```json
  [
    {
      "id": 1,
      "title": "debitis ad repellendus facere reprehenderit",
      "text": "Quisquam est fuga dolor harum eum et. Voluptatem blanditiis qui sit nisi. Maiores quasi in repellendus numquam. [...]",
      "premiumRequired": false,
      "freeOnFirstDay": false,
      "commentsEnabled": true,
      "createdAt": "2022-05-31T...",
      "updatedAt": "2022-05-31T..."
    },
    {
      "id": 2,
      "title": "qui iusto ducimus fuga dicta impedit",
      "text": "Eligendi reprehenderit id impedit laborum in. Mollitia sunt illo et. Omnis nulla harum velit placeat ducimus qui rerum. [...]",
      "premiumRequired": false,
      "freeOnFirstDay": false,
      "commentsEnabled": false,
      "createdAt": "2022-05-31T...",
      "updatedAt": "2022-05-31T..."
    },
    STB.
  ]
  ```

### `3. feladat: GET /articles (3 pont)`

Lekéri a cikkek ID-jét és címét, továbbá megadja, hogy a cikk jelen pillanatban ingyenes-e (`free_now`). Itt már NEM elég csak a `premiumRequired` mezőt nézni, ahogy azt az első feladatban tetted! Ugyanis ha a cikk előfizetéshez van kötve (a `premiumRequired` mezőjének értéke igaz), DE a `freeOnFirstDay` mezőjének értéke is igaz, akkor az azt jelenti, hogy az előfizetéshez kötöttség ellenére az első nap ingyenesen, korlátozás nélkül elolvasható a cikk. Az "első nap" a `createdAt` mezőben rögzített időpont óta eltelt időt jelenti. Két dátum közti különbség kiszámításához alapul veheted ezt: https://stackoverflow.com/a/15289883, és használhatod a [Date() constructor-t](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date/Date).

- Minta kérés: `GET http://localhost:4000/articles`
- Válasz megfelelő kérés esetén: `200 OK`
  ```json
  [
    {
      "id": 1,
      "title": "debitis ad repellendus facere reprehenderit",
      "free_now": true
    },
    {
      "id": 2,
      "title": "qui iusto ducimus fuga dicta impedit",
      "free_now": true
    },
    {
      "id": 3,
      "title": "et dolores dolor itaque",
      "free_now": false
    },
    {
      "id": 4,
      "title": "non a perferendis officia voluptatem qui",
      "free_now": true
    },
    {
      "id": 5,
      "title": "nemo",
      "free_now": true
    },
    {
      "id": 6,
      "title": "est ab dolores doloremque quo",
      "free_now": true
    }
  ]
  ```

### `4. feladat: GET /articles/:id (6 pont)`

Lekér egy cikket a megadott ID alapján.

- A cikk alapadataihoz (mezőihez) hozzá kell venni a cikk szerzőit és a cikkhez írt hozzászólásokat is a minta válaszban lévő `Authors` és `Comments` rész alapján.
  - Az `Authors`-ban lévő felhasználóknak **csak** az `id`, `email` és `name` mezőit add meg!
  - A `Comments`-ben lévő hozzászólásoknak **csak** az `id`, `text` és `UserId` mezőit add meg!
- Továbbá kezelni kell az előfizetéshez kötött cikkekkel járó korlátozásokat is. Ez azt jelenti, hogyha egy cikk nem tekinthető meg ingyenesen (lásd az előző feladatban a `free_now` részt), akkor a vendégeknek / nem prémium szintű felhasználóknak nem jelenik meg a cikk teljes tartalma, csak az első 96 karakter és három pont, a következő minta szerint: `<text mező első 96 karaktere>...`. Mivel a `text`-re egy legalább 128 karakter hosszúságot megkövetelő validátor van beállítva, ezért nem kell foglalkozni azzal az esettel, hogy mi van akkor, ha 96 karakternél rövidebb.
  - Értelemszerűen ebből az is következik, hogy ehhez a végponthoz szükséges egy opcionális hitelesítés.
  - Ha a hitelesített felhasználó újságíró (`isJournalist`), akkor bármilyen cikket megtekinthet prémium tagságtól függetlenül.
- Minta kérés: `POST http://localhost:4000/articles/3`
- Minta válasz: `200 OK`
  ```json
  {
    "id": 3,
    "title": "et dolores dolor itaque",
    "text": "Eos reprehenderit reprehenderit placeat. Eveniet itaque veniam occaecati voluptates. Voluptas rerum quisquam perspiciatis sequi est repellat fugit nostrum nesciunt. Modi occaecati modi ut. Praesentium eos modi sed aliquam sapiente porro ea nobis consequatur. [...]",
    "premiumRequired": true,
    "freeOnFirstDay": false,
    "commentsEnabled": true,
    "createdAt": "2022-05-31T...",
    "updatedAt": "2022-05-31T...",
    "Authors": [
      {
        "id": 2,
        "email": "journalist2@szerveroldali.hu",
        "name": "Journalist2"
      },
      {
        "id": 1,
        "email": "journalist1@szerveroldali.hu",
        "name": "Journalist1"
      },
      {
        "id": 4,
        "email": "journalist4@szerveroldali.hu",
        "name": "Journalist4"
      }
    ],
    "Comments": [
      {
        "id": 11,
        "text": "Et exercitationem illum deserunt. Tempora consequatur quis quasi placeat sit molestiae quas et. Et a eveniet et. Doloremque dolor sunt in et aut esse delectus. Culpa nulla voluptatum aut eligendi nam et ipsa. Dolor saepe sed natus animi tempore sunt eligendi.",
        "UserId": 4
      },
      {
        "id": 12,
        "text": "Sed illum eos odit modi. Nihil reiciendis rerum. Quis dolores illo et optio quo ea. Laboriosam voluptas ut explicabo architecto a. Natus quia distinctio sunt iusto earum officiis aliquam sint.",
        "UserId": 4
      }
    ]
  }
  ```
- Minta válasz, ha nem tekintheti meg a teljes cikket: `200 OK`
  ```json
  {
    "id": 3,
    "title": "et dolores dolor itaque",
    "text": "Eos reprehenderit reprehenderit placeat. Eveniet itaque veniam occaecati voluptates. Voluptas re...",
    STB.
  }
  ```
  - Nem jelenik meg a cikk teljes tartalma
- _Tipp:_ Az `Authors` és a `Comments` lekérésére több mód is van:
  - a Sequelize kérés beállításaiban az `include` használatával és egyben kéred le őket a cikkel;
  - lekéred az alap cikket, majd külön a relációkat, és valahogy összefésülöd őket egy megfelelő válasszá.
- _Tipp:_ Opcionális hitlesítéshez használhatod ezt a middleware-t:
  ```js
  const authMiddleware = require("../middlewares/auth");
  // ...
  const optionalauthMiddleware = (req, res, next) =>
    authMiddleware(req, res, (err) => next());
  ```
  - Ennek eredményeként sikeres hitelesítéskor a JWT payload elérhetővé válik a `req.user` alatt.

### `5. feladat: PATCH /articles/:id (3 pont)`

Módosít egy meglévő cikket. Cikket csak hitelesített újságírók (`isJournalist`) módosíthatnak. Ha egy újságíró sikeresen módosít egy cikket, akkor bekerül a cikk szerzői/közeműködői (`Authors`) közé.

- Minta kérés: `PATCH http://127.0.0.1:4000/articles/3`
  ```json
  {
    "title": "valami"
  }
  ```
- Válasz megfelelő kérés esetén: `200 OK`
  ```json
  {
    "id": 3,
    "title": "valami",
    "text": "Eos reprehenderit reprehenderit placeat. Eveniet itaque veniam occaecati voluptates. Voluptas rerum quisquam perspiciatis sequi est repellat fugit nostrum nesciunt. Modi occaecati modi ut. Praesentium eos modi sed aliquam sapiente porro ea nobis consequatur. [...]",
    "premiumRequired": true,
    "freeOnFirstDay": false,
    "commentsEnabled": true,
    "createdAt": "2022-05-31T...",
    "updatedAt": "2022-05-31T..."
  }
  ```
- Válasz, ha a megadott id-vel nem létezik cikk: `404 NOT FOUND`
- Válasz hitelesítetlen kérés esetén: `401 UNAUTHORIZED`
- Válasz hitelesített, de jogosulatlan kérés esetén (ha nem újságíró a felhasználó): `403 FORBIDDEN`

### `6. feladat: DELETE /articles/:id/delete-comments (3 pont)`

Törli a cikkhez tartozó összes hozzászólást. A hozzászólásokat csak hitelesített újságírók (`isJournalist`) törölhetik ki.

- Minta kérés: `DELETE http://localhost:4000/articles/3/delete-comments`
- Válasz hitelesítetlen kérés esetén: `401 UNAUTHORIZED`
- Válasz hitelesített, de jogosulatlan kérés esetén (ha nem újságíró a felhasználó): `403 FORBIDDEN`
- Válasz, ha a megadott id-vel nem létezik cikk: `404 NOT FOUND`
- Válasz megfelelő kérés esetén, ha voltak hozzászólások, amiket törölni kellett: `200 OK`
- Válasz megfelelő kérés esetén, ha nem voltak hozzászólások, amiket törölni lehetett volna: `204 NO CONTENT`

### `7. feladat: POST /articles/:id/comment (3 pont)`

Hozzászólás írása egy cikkhez. A végpont hitelesítéshez kötött, mivel hozzászólást csak felhasználók írhatnak (az most lényegtelen, hogy újságíró-e).

- Minta kérés: `POST http://localhost:4000/articles/3/comment`
  ```json
  {
    "text": "teszt komment"
  }
  ```
- Válasz megfelelő kérés esetén: `201 CREATED`
  ```json
  {
    "id": 33,
    "text": "teszt komment",
    "ArticleId": 3,
    "UserId": 2,
    "updatedAt": "2022-05-31T...",
    "createdAt": "2022-05-31T..."
  }
  ```
- Válasz hitelesítetlen kérés esetén: `401 UNAUTHORIZED`
- Válasz, ha a megadott id-vel nem létezik cikk: `404 NOT FOUND`
- Válasz, ha a felhasználó némítva van (`isMuted`) vagy a cikkhez nincsenek engedélyezve a kommentek (`commentsDisabled`): `403 FORBIDDEN`
- Válasz hibás kérés esetén (hiányzó/hibás adatok, stb): `400 BAD REQUEST`

### `8. feladat: POST /set-muted (2 pont)`

Beállítja, hogy egy felhasználó némítva legyen-e. A végpontot csak hitelesített újságírók (`isJournalist`) használhatják.

- Minta kérés: `POST http://localhost:4000/set-muted`
  ```json
  {
    "targetUserId": 2,
    "isMuted": false
  }
  ```
- Válasz hitelesítetlen kérés esetén: `401 UNAUTHORIZED`
- Válasz hitelesített, de jogosulatlan kérés esetén (ha nem újságíró a felhasználó): `403 FORBIDDEN`
- Válasz, ha a megadott id-vel nem létezik felhasználó: `404 NOT FOUND`
- Válasz megfelelő kérés esetén: `200 OK`

### `9. feladat: GET /stats (6 pont)`

Különféle statisztikák. A végponthoz semmilyen hitelesítés sem kell.

- A kért adatok:
  - `freeArticlesCount`: hány db ingyenes cikk van (elég csak a `premiumRequired` mezőt nézni)
  - `paidArticlesCount`: hány db fizetős cikk van (elég csak a `premiumRequired` mezőt nézni)
  - `currentlyFreePaidArticlesCount`: hány db olyan fizetős cikk van, ami a kérés pillanatában ingyenesen olvasható (nem elég csak a `premiumRequired` mezőt nézni, hanem a `freeOnFirstDay` mezőt is hozzá kell venni - lásd a 3. feladatban a `free_now` mezőt a részletekért)
  - `currentlyFreeArticlesPercentage`: a kérés pillanatában ingyenesen elérhető cikkek hány %-át teszik ki az összes cikknek (fontos, hogy ebben benne vannak a teljesen ingyenes cikkek, és azok is, amelyek csak első nap ingyenesek - az adat a kérés pillanatára vonatkozik!)
  - `commentsCountByPremiumUsers`: hány db hozzászólás származik olyan felhasználótól, aki prémium tag (`isPremium`)
  - `longestArticleId`: azon cikk ID-je, amelyik a leghosszabb (`text` mező hossza). Ha több ilyen is van, elég csak az egyik.
  - `commentedArticlesCount`: hány olyan cikk található az adatbázisban, amelyhez legalább 3 kommentet írtak.
- Minta kérés: `GET http://localhost:4000/stats`
- Minta válasz: `200 OK`
  ```json
  {
    "freeArticlesCount": 3,
    "paidArticlesCount": 3,
    "currentlyFreePaidArticlesCount": 2,
    "currentlyFreeArticlesPercentage": 83.33333333333334,
    "commentsCountByPremiumUsers": 7,
    "longestArticleId": 3,
    "commentedArticlesCount": 5
  }
  ```
