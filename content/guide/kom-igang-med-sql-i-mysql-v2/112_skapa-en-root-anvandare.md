---
author: mos
revision:
    "2021-12-20": "(C, mos) Omskriven inför v2 och MariaDB."
    "2019-01-24": "(B, mos) Bort med överflödigt ;."
    "2019-01-21": "(A, mos) Första versionen."
...
Skapa en root användare
==================================

Vi skall skapa en ny användare i databasen, en användare som har samma behörighet som root användaren.

Spara SQL-koden du gör i en fil och döp den till `create-user.sql`.

Troligen har du redan skapat en sådan användare när du installerade databasen, men här gör vi det en gång till och nu sparar vi alla SQL-konstruktioner i en fil. Att spara konstruktionerna i en fil gör det enkelt att dokumentera, titta tillbaka och återskapa en databas.



Skapa en ny användare {#createuser}
--------------------------------------

Dokumentationen för att skapa en ny användare finns i [CREATE USER](https://mariadb.com/kb/en/create-user/).

Jag tänker skapa användaren `maria@localhost` och ge användaren fulla rättigheter. Att ge fulla rättigheter gör saker enklare när vi jobbar i kursen. Normalt sett hade man troligen begränsat vilka rättigheter som användaren har, vilka databaser och tabeller som den kan använda och från vilka maskiner den kan ansluta.

Öppna terminalklienten och skriv följande SQL-kod för att skapa en användare som kan ansluta från localhost vilket innebär att databasservern måste finnas på din localhost.

Du kan döpa din användare till vad du vill, men jag kör på "maria".

```text
CREATE USER 'maria'@'localhost'
IDENTIFIED BY 'P@ssw0rd!'
;
```

Ge användaren fullständiga rättigheter på alla databaser `*.*`, det blir i princip samma rättigheter som en root-användare som har tillgång till allt.

```text
GRANT ALL PRIVILEGES
ON *.* TO 'maria'@'localhost'
WITH GRANT OPTION
;
```

Kommandot [GRANT finns beskrivet i manualen](https://mariadb.com/kb/en/grant/).

Bra, då har vi en användare som har fulla rättigheter i databasservern.

För att vara på den säkra sidan så flushar vi alla privileges så att användaren kan användas direkt. Kommandot [FLUSH finns beskrivet i dokumentationen](https://mariadb.com/kb/en/flush/)]

```text
FLUSH PRIVILEGES;
```



Använd den nya användaren {#useuser}
--------------------------------------

Nu kan vi använda den nya användaren. Pröva att göra det i terminalklienten. Logga in i terminalklienten med din nyskapade användare.

```text
mariadb -u maria
```

Det kan se ut så här när du kollar vilken användare du är inloggad med.

```text
MariaDB [(none)]> SELECT USER();
+-----------------+
| USER()          |
+-----------------+
| maria@localhost |
+-----------------+
```

Du kan även kolla vilka rättigheter användaren har med följande kommando.

```text
SHOW GRANTS;
```

Det kan vara bra att kontrollera sådant om man råkar ut för behörighetsproblem.



Ta bort en användare {#dropuser}
--------------------------------------

Om du behöver ta bort användaren och skapa den igen så kan du droppa (ta bort) den så här.

Kommandot [`DROP USER` finns beskrivet i manualen](https://mariadb.com/kb/en/drop-user/).

```text
MariaDB [(none)]> DROP USER IF EXISTS 'maria'@'localhost';
Query OK, 0 rows affected (0.000 sec)
```

En god idé är att placera denna raden överst i din fil med SQL-kommandon, då kan du alltid köra hela skriptet som en enhet för att återskapa din användare. Om användaren redan finns kommer den att tas bort och då kan sedan återskapa den.



Kontrollera ditt skript {#skript}
--------------------------------------

Dubbelkolla att du har skrivit in alla SQL-kommandon i ditt skript. Detta är viktigt om du senare behöver återställa din databas.

Du bör nu kunna köra skriptet som helhet, antingen via Workbench eller via terminalen. Du kan till exempel köra hela skriptet så här i terminalklienten.

```text
mariadb < create-user.sql
```

Har du gjort rätt så kommer användaren att tas bort och återskapas och resultatet kommer att skrivas ut.

Kontrollera alltid att det inte skrivs ut felmeddelande i skriptet, då behöver du felsöka genom att avgränsa och rätta till problemet. Felsökning kan man göra genom att köra varje kommando för sig och börja med det översta kommandot i filen.



Problem och facit? {#problem}
--------------------------------------

Om du får problem så finns det i detta fallet ett facit som du kan studera i filen `example/sql/v2/create-user-maria.sql`.

Troligen kan du skriva lite mer kommentarer i ditt skript, det kan underlätta när man går tillbaka till ett skript för att se vad det gör.

Det kan även testa att köra skriptet så här.

```text
# Stå i rooten av ditt kursrepo
mariadb < example/sql/v2/create-user-maria.sql
```
