# Szerveroldali webprogramozás 2021/22/2 - Laravel beadandó

:hourglass: **HATÁRIDŐ: 2022. április 19. (kedd) 23:59** (a tavaszi szünet vége)

## Tartalomjegyzék

- [Szerveroldali webprogramozás 2021/22/2 - Laravel beadandó](#szerveroldali-webprogramozás-2021222---laravel-beadandó)
  - [Tartalomjegyzék](#tartalomjegyzék)
  - [Minimum követelmények](#minimum-követelmények)
  - [További követelmények](#további-követelmények)
  - [Feladatok (60 pont)](#feladatok-60-pont)
    - [1. feladat: Adatmodellek és relációk (2 pont)](#1-feladat-adatmodellek-és-relációk-2-pont)
      - [Adatmodellek](#adatmodellek)
      - [Relációk](#relációk)
    - [2. feladat: Seeder (4 pont)](#2-feladat-seeder-4-pont)
    - [3. feladat: Űrlapkezelő főmenü (3 pont)](#3-feladat-űrlapkezelő-főmenü-3-pont)
    - [4. feladat: Új űrlap létrehozása (12 pont)](#4-feladat-új-űrlap-létrehozása-12-pont)
    - [5. feladat: Űrlapok kezelése](#5-feladat-űrlapok-kezelése)
      - [5/a: Űrlapkezelő (6 pont)](#5a-űrlapkezelő-6-pont)
      - [5/b: Űrlap módosítása (9 pont)](#5b-űrlap-módosítása-9-pont)
      - [5/c: Statisztika és válaszok megtekintése (12 pont)](#5c-statisztika-és-válaszok-megtekintése-12-pont)
    - [6. feladat: Űrlap kitöltése (12 pont)](#6-feladat-űrlap-kitöltése-12-pont)
  - [Hasznos hivatkozások](#hasznos-hivatkozások)

## Minimum követelmények

```diff
- FIGYELEM! A beadandódnak az alább felsorolt ÖSSZES követelményt teljesítenie kell, különben a megoldást nem értékeljük!
```

- **A beadandót a kijelölt határidőn belül be kell adni a Canvas felületen!**
  ```diff
  - FIGYELEM! A Canvas beadási felülete a határidő lejártakor automatikusan LEZÁR!                            
  - Ez azt jelenti, hogy a határidő lejárta után NINCS lehetőség beadásra, már 0:00-tól sem!                  
  - Haladékra csak kivételes és igazolt esetben van lehetőség a gyakorlatvezetőd egyéni elbírálásától függően!
  - Ha valaki kicsúszik a határidőből, akkor nem teljesítette beadandót, ebből kifolyólag pedig a tárgyat sem,
  - hiszen a beadandó a tárgy teljesítésének egyik alapkövetelménye!                                          
  ```
- Kötelező a kezdőcsomag használata! A kezdőcsomag [INNEN](https://github.com/szerveroldali/laravel_kezdocsomag_2021-22-2/archive/refs/heads/main.zip) tölthető le.
- Tilos további Composer-es csomagokat telepíteni a UI csomagokon kívül! A feladat kényelmesen megoldható azokkal az alap csomagokkal, amiket a kezdőcsomag is biztosít. NPM-es csomagok telepíthetők, frontend szabadon választható.
- Az adattároláshoz SQLite adatbázist kell használni! A beadott alkalmazás SQLite kapcsolatra legyen beállítva (ez a kezdőcsomag alapértelmezett viselkedése)!
- Az alkalmazás a beadott zip-ből kicsomagolva az operációs rendszernek megfelelő `init.bat` / `init.sh` fájlokat futtatva  mindenféle hiba nélkül el kell induljon!
  - Ezek a fájlok a beadandó inicializációs parancsait tartalmazzák. Az `init.bat`-ot Windows-on, az `init.sh`-t pedig Linux-on vagy macOS-en kell használni. 
  - Mielőtt beadod a feladatot, csomagold ki a `zipfiles` mappában lévő zip-et, kattints a benne lévő init fájlra, majd várd meg, hogy lefussanak a benne lévő inicializáló parancsok! Ezt követően pedig **teszteld**, hogy az alkalmazás rendesen működik-e! Ezzel kizárod az inicializációs hibákat és arról is meggyőződsz, hogy mindent megfelelően beadtál-e.
- A hibátlan inicializáción felül elvárás az is, hogy az alkalmazás működjön, és ne legyenek benne olyan nagyobb, fatális hibák, amik miatt a teljes alkalmazás vagy annak egy jelentős része nem használható. Értelemszerűen ez a kisebb hibákat nem érinti, azok csak pontlevonást jelentenek az adott feladatnál.
- Kötelező mellékelni a munka tisztaságáról szóló **STATEMENT.txt** nyilatkozatot! A nyilatkozatot a `php artisan zip` automatikusan kezeli! A nyilatkozat szövege:
  ```
  NYILATKOZAT
  ===========

  Én, <NÉV> (Neptun kód: <NEPTUN KÓD>) kijelentem, hogy ezt a megoldást én küldtem be a Szerveroldali webprogramozás Laravel beadandó feladatához.
  A feladat beadásával elismerem, hogy tudomásul vettem a nyilatkozatban foglaltakat.

  - Kijelentem, hogy ez a megoldás a saját munkám.
  - Kijelentem, hogy nem másoltam vagy használtam harmadik féltől származó megoldásokat.
  - Kijelentem, hogy nem továbbítottam megoldást hallgatótársaimnak, és nem is tettem azt közzé.
  - Tudomásul vettem, hogy az Eötvös Loránd Tudományegyetem Hallgatói Követelményrendszere (ELTE szervezeti és működési szabályzata, II. Kötet, 74/C. §) kimondja, hogy mindaddig, amíg egy hallgató egy másik hallgató munkáját - vagy legalábbis annak jelentős részét - saját munkájaként mutatja be, az fegyelmi vétségnek számít.
  - Tudomásul vettem, hogy a fegyelmi vétség legsúlyosabb következménye a hallgató elbocsátása az egyetemről.
  ```
- Tilos beadni a **vendor** és/vagy a **node_modules** mappát!
- A felhasználói felületet legalább annyira ki kell dolgozni, hogy a funkciók a frontend-en keresztül is elérhetőek legyenek és beadandó böngészőből is tesztelhető legyen a kódban való kutatás nélkül! Tipikusan pl.: legyen navbar, működjenek a linkek, gombok, stb! A frontendhez használt technológia nincs megkötve, tehát használhatsz Bootstrap-et, Tailwind-et, stb!

## További követelmények

- Az űrlapokon keresztül küldött adatokat minden esetben validálni kell szerveroldalon! HTML szintű validáció (pl. required attribútum) ne is legyen a kódban! Nem a HTML tag-ek ismeretét szeretnénk számonkérni egy szerveroldali tárgyon, hanem a Laravel validációjának megfelelő alkalmazását!
- Az űrlapok legyenek állapottartók, vagyis ha a validator visszadobja a szerver felé intézett kérést, akkor ne vesszenek el az addig bevitt adatok!
- A tárgy követelményeivel összhangban a beadandón legalább a pontok 40%-át (24 pont) meg kell szerezni ahhoz, hogy a beadandó témaköre sikeres legyen!

## Feladatok (60 pont)

A feladat, hogy [ezen kezdőcsomagból kiindulva](https://github.com/szerveroldali/laravel_kezdocsomag_2021-22-2/archive/refs/heads/main.zip) készíts egy űrlapkezelő rendszert, ami gyakorlatilag a Google Forms egyszerűsített változata. A felhasználók létre tudnak hozni űrlapokat különféle típusú kérdésekkel, majd a létrejött űrlap linkjét meg tudják osztani másokkal, akik kitölthetik az adott űrlapot. Az űrlap létrehozója később áttekintheti a kérdésekre adott válaszokat az űrlapkezelő felületen.

:package: A beadandót a `php artisan zip` parancs segítségével be kell csomagolni, majd a létrejött zip fájlt a Canvas rendszerben be kell adni a kijelölt feladathoz a megadott határidőig! A határidő lejárta után a Canvas lezár, ezért onnantól nincs lehetőséged beadásra, ezért ügyelj arra, hogy ne hagyd az utolsó pillanatra a beadást! A legutoljára beadott megoldást fogjuk értékelni, és részpontokat is adunk!

:bulb: Ha a munkád közben bármilyen kérdésed adódik, fordulj bizalommal a gyakorlatvezetődhöz segítségért!

### 1. feladat: Adatmodellek és relációk (2 pont)

Hozd létre a következő adatmodelleket a kért mezőkkel! Egy mező csak akkor lehet nullable, ha ezt a feladat külön kéri! Az `id`, `created_at`, `updated_at` mezők is szükségesek, ezeket a Laravel magától kezeli. A modellek létrehozását követően add meg a köztük lévő relációkat is, mind a migration, mind pedig a model fájlokban!

#### Adatmodellek

- `User` (ez már alapból létezik)
- `Form` (az űrlap/kérdőív alapadatai)
  - `id`
  - `title` (string: 255) (űrlap címe)
  - `expires_at` (datetime) (meddig tölthető ki)
  - `auth_required` (boolean, default: false) (bejelentkezéshez kötött-e a kitöltés)
  - `created_by` (integer, foreign key, references to `id` on `users` table) (a felhasználó azonosítója, aki az űrlapot létrehozta)
  - `created_at`, `updated_at`
- `Question` (az űrlapokban előforduló lehetséges kérdések és azok típusai)
  - `id`
  - `form_id` (integer, foreign key, references to `id` on `forms` table) (űrlap azonosítója, amihez a kérdés tartozik)
  - `question` (string: 255) (kérdés szövege)
  - `answer_type` (enum: `TEXTAREA`, `ONE_CHOICE`, `MULTIPLE_CHOICES`) (válasz típusa: szöveges, egy válaszlehetőség, több válaszlehetőség)
  - `required` (boolean, default: true) (kötelező-e az adott kérdést megválaszolni az űrlap kitöltésekor)
  - `created_at`, `updated_at`
- `Choice` (válaszlehetőségek, ha a kérdés feleletválasztós)
  - `id`
  - `question_id` (integer, foreign key, references to `id` on `questions` table) (a kérdés azonosítója, amihez a válaszlehetőség tartozik)
  - `choice` (string: 255) (a válaszlehetőség szövege)
  - `created_at`, `updated_at`
- `Answer` (a kitöltők által adott válaszok, minden válasz egy rekord)
  - `id`
  - `question_id` (integer, foreign key, references to `id` on `questions` table) (a kérdés azonosítója, amihez a kitöltő által megadott válasz tartozik)
  - `user_id` (integer, foreign key, references to `id` on `users` table) (a felhasználó azonosítója, aki megválaszolta a kérdést, vendég esetén null)
  - `choice_id` (integer, foreign key, references to `id` on `choices` table) (a válaszlehetőség azonosítója, ami be lett jelölve, ha `ONE_CHOICE`/`MULTIPLE_CHOICES` típusú a kérdés)
  - `answer` (text) (a válasz szövege, ha `TEXTAREA` típusú a kérdés)
  - `created_at`, `updated_at`

Ha több válaszlehetőség van, akkor több `Answer` kell `choice_id`-val és null-os answerrel.

#### Relációk

- `User` 1-N `Form`
- `Form` 1-N `Question`
- `Question` 1-N `Choice`
- `Question` 1-N `Answer`

### 2. feladat: Seeder (4 pont)

- Az alkalmazás legyen feltölthető adatokkal seeder segítségével. Ha több különálló seeder van, akkor ezek legyenek egyesítve a `DatabaseSeeder.php`-ban [`call`](https://laravel.com/api/8.x/Illuminate/Database/Seeder.html#method_call)/[`callWith`](https://laravel.com/api/8.x/Illuminate/Database/Seeder.html#method_callWith) hívások segítségével!
- A seedelés lehetőleg minél több esetet fedjen le, tehát mindenféle model, ami az alkalmazásban van, az kerüljön seedelésre, valamint a köztük lévő kapcsolatok (relációk) is legyenek létrehozva.
- A seeder ezzel az egy paranccsal legyen hívható: `php artisan db:seed` (ez a `DatabaseSeeder.php`-t hívja meg)!
- :warning: A felhasználók az egyszerűség kedvéért **csak ezek lehetnek** (email - jelszó):
  - *user1@szerveroldali.hu - password*
  - *user2@szerveroldali.hu - password*
  - *user3@szerveroldali.hu - password*
  - stb.

### 3. feladat: Űrlapkezelő főmenü (3 pont)

Az alkalmazás gyökér útvonala (http://localhost:8000) irányítson át az űrlapkezelő felületre. A felületet csak bejelentkezett felhasználók használhatják, ezért ha vendég nyitja meg az oldalt, akkor a bejelentkező felületre kell átirányítani.

Az űrlapkezelő oldalon alapvetően két fő menüpontot kell biztosítani:
- Egy linket, amire kattintva a bejelentkezett felhasználó új űrlapot tud létrehozni;
- Egy olyan linket, amin a bejelentkezett felhasználó által korábban létrehozott űrlapok kezelhetők, tekinthetők át:
  - módosítás, 
  - kérdésekre adott válaszok megtekintése.

### 4. feladat: Új űrlap létrehozása (12 pont)

Készítsd el a felületet, ahol új űrlapot lehet felvenni! Az első részben az űrlap alapadatait kell megadni:
- mi a címe,
- kitöltése bejelentkezéshez kötött-e,
- mikor jár le
  - tipp: használhatod a [datetime-local](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/datetime-local) mezőtípust a lejárathoz

Ezt követően az űrlaphoz tartozó kérdéseket kell felvenni. Egy űrlaphoz N db kérdés tartozhat, és egy feleletválasztós kérdéshez is N db válaszlehetőséget lehet rendelni. Ez azt jelenti, hogy nem tudsz hozzá megadni egy statikus form-ot, hanem dinamikusan kell kezelned a mezőket. Ennek többféle megközelítése is lehetséges, [ide kattintva](https://totadavid.hu/files/dinamikus_form_pelda.zip) adunk egy nagyon leegyszerűsített példát, amiből ki tudsz indulni.

Az űrlap létrehozását követően irányítsd át a felhasználót egy oldalra, ahol jelenítsd meg neki a létrejött űrlap linkjét, és tudasd vele, hogy azt kell megosztania másokkal. Ha valaki majd megnyitja azt a linket, akkor ott fogja tudni kitölteni a kérdőívet.

### 5. feladat: Űrlapok kezelése

#### 5/a: Űrlapkezelő (6 pont)

Készíts egy olyan oldalt, ahol a felhasználó számára listázod az általa létrehozott űrlapokat!
- Az űrlapok az `updated_at` mező alapján időrendileg csökkenő sorrendben legyenek, vagyis a legfrissebb legyen legelöl! A listában jelenjen meg az űrlap címe, és a létrehozásának az ideje.
- Egy oldalon egyszerre legfeljebb 5 űrlap jelenjen meg, vagyis használj *pagination*-t!

Az űrlapkezelő listájában egy űrlapra kattintva jöjjön be annak az adatlapja. Az adatlapot a következő két részfeladat taglalja.

#### 5/b: Űrlap módosítása (9 pont)

Az adatlapon kínáld fel a felhasználónak a módosítás lehetőségét! A módosítás azt jelenti, hogy az űrlap adatai és a hozzá tartozó kérdések is módosíthatók, **DE** csak abban az esetben tegyük lehetővé a módosítást, ha még senki sem küldött be választ az űrlaphoz! Ha már érkeztek válaszok, akkor tudatni kell a felhasználóval, hogy emiatt már nem módosíthatja az űrlapot, hiszen az elrontaná az addigi kitöltéseket.

#### 5/c: Statisztika és válaszok megtekintése (12 pont)

Az űrlap adatlapján a módosításon túl meg kell jeleníteni a hozzá tartozó kérdéseket is, valamint az ezekre adott válaszokat. Ha egy kérdéshez még nincsenek válaszok, abban az esetben erről is tájékoztasd a felhasználót!

A kérdésekhez tartozó válaszokat a következő módon kell megjeleníteni:
- Kifejtős kérdés esetén egyszerűen listázd ki a szöveges válaszokat, továbbá jelenítsd meg azt is, hogy ki írta az adott választ (felhasználónév/"Vendég")
- Feleletválasztós kérdés esetén jelenítsd meg az összes lehetséges válaszlehetőséget (Choice), majd utána zárójelben, hogy az adott lehetőséget hányan választották! A válaszlehetőségek a rájuk adott válaszok száma szerint csökkenő sorrendben legyenek listázva!

> Megjegyzés: tegyük fel, hogy nem lesz sok szöveges válasz, így ha az összes választ kilistázod a kérdés alá, az nem probléma.

### 6. feladat: Űrlap kitöltése (12 pont)

Az űrlap linkjét megnyitva megjelenik a kitöltő felület. 
- Ha a megadott űrlap nem létezik, 404-es hibakódot kell adni.
- Ha kitöltése bejelentkezéshez kötött, de a kitöltő nincs bejelentkezve, akkor előbb a login felületre kell irányítani.
- Ha az űrlap lejárt (`expired_at` mező), akkor ezt hibaként jelezni kell a kitöltőnek.
- Egy űrlapot többször is ki lehet tölteni, mind vendégnek, mind felhasználónak.
- Beküldéskor a validálásnál a következő szempontokra figyelj:
  - ki kell kényszeríteni, hogy a `required` kérdésekre a kitöltő mindenképpen válaszoljon,
  - kezelni kell azt az esetet is, hogy a feleletválasztós kérdésekre biztosan csak a megadott válaszlehetőségek valamelyikét lehessen megjelölni,
    - itt az a lényeg, hogy a szerver felé küldött kérés manipulálásával ne legyen megkerülhető a rendszer
  - ha egy kérdésnél csak egy válaszlehetőséget lehet kiválasztani (`ONE_CHOICE`), akkor ott ne lehessen több választ megadni,
  - ha az űrlap a kitöltés közben lejárt, akkor erről is tájékoztatni kell a kitöltőt!

## Hasznos hivatkozások

Az alábbiakban adunk néhány hasznos hivatkozást, amiket érdemes szemügyre venni a beadandó elkészítésekor.

- [Németh Tamás órai anyagai 2021/22/2](https://github.com/anonymus1928/Szerveroldali)
- [Végh Barnabás órai anyagai 2021/22/2](https://github.com/vegh-barnabas/szerveroldali-webprog)
- [Tóta Dávid órai alkalmazása 2021/22/1](https://github.com/szerveroldali/2021-22-1/tree/main/esti_3_4_csut_19_30/laravel)
- [Laravel nyelvi csomag - magyarosításhoz](https://github.com/Laravel-Lang/lang)
- Tantárgyi Laravel jegyzetek:
  - [Kimenet generálása](http://webprogramozas.inf.elte.hu/#!/subjects/webprog-server/handouts/laravel-01-kimenet)
  - [Bemeneti adatok, űrlapfeldolgozás](http://webprogramozas.inf.elte.hu/#!/subjects/webprog-server/handouts/laravel-02-bemenet)
  - [Adattárolás, egyszerű modellek](http://webprogramozas.inf.elte.hu/#!/subjects/webprog-server/handouts/laravel-03-adatt%C3%A1rol%C3%A1s)
  - [Relációk a modellek között](http://webprogramozas.inf.elte.hu/#!/subjects/webprog-server/handouts/laravel-04-rel%C3%A1ci%C3%B3k)
  - [Hitelesítés és jogosultságkezelés](http://webprogramozas.inf.elte.hu/#!/subjects/webprog-server/handouts/laravel-05-hiteles%C3%ADt%C3%A9s)
  - [GitHub-os Laravel jegyzet](https://github.com/totadavid95/szerveroldali-21-tavasz/blob/main/Laravel.md)
- Hivatalos dokumentációk
  - [Laravel dokumentáció](https://laravel.com/docs)
    - [Blade direktívák](https://laravel.com/docs/8.x/blade)
    - [Resource Controllers](https://laravel.com/docs/8.x/controllers#resource-controllers)
    - [Validációs szabályok](https://laravel.com/docs/8.x/validation#available-validation-rules)
    - [Migrációknál elérhető mezőtípusok](https://laravel.com/docs/8.x/migrations#available-column-types)
  - [Laravel API dokumentáció](https://laravel.com/api/master/index.html)
  - [PHP dokumentáció](https://www.php.net/manual/en/)
  - [Bootstrap 5 dokumentáció](https://getbootstrap.com/docs/)
- Programok, fejlesztői eszközök
  - [Automatikus PHP és Composer telepítő](https://github.com/totadavid95/PhpComposerInstaller)
  - [Visual Studio Code](https://code.visualstudio.com/)
    - [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)
    - [Laravel Extension Pack](https://marketplace.visualstudio.com/items?itemName=onecentlin.laravel-extension-pack)
  - [DB Browser for SQLite](https://sqlitebrowser.org/)
- További CSS framework tippek:
  - [Tailwind CSS](https://tailwindcss.com/)
  - [Material Bootstrap](https://mdbootstrap.com/)
  - [Material UI, React-hez](https://material-ui.com/)
  - [Fontawesome ikonkészlet](https://fontawesome.com/)
  - [Bulma](https://bulma.io/)
