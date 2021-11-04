---
author:
    - aar
revision:
    "2021-10-29": "(C, aar) Slog ihop canvas inlämning med kmom01."
    "2020-11-06": "(B, aar) Ready for HT20."
    "2019-11-01": "(A, aar) Första versionen."
...
Kmom02: Docker
==================================

Vi packar in vår kod i en Docker container för att underlätta utveckling, driftsättning och körning av vår applikation.

<!-- more -->

[WARNING]
Kursmoment är uppdateras. Saker kan förändras.
Fortsätt på egen risk!
[/WARNING]

[FIGURE src="https://pics.me.me/it-works-on-my-machine-then-well-ship-your-machine-62072263.png"]


[INFO]
Innan ni sätter igång med kursmomentet kolla att ert Microblog repo är synkat med originalet, [Syncing a fork](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork).
[/INFO]



## Vad är Docker? {#docker}

En snabb översikten av vad Docker är kan vi hitta på [Dockers egna webbsida](https://www.docker.com/resources/what-container). Docker är en container teknologi som liknar en avskalad virtuella maskin. Vad tillför det till oss som utvecklare?

Docker låter utvecklare att utveckla och driftsätta applikationer i virtuella container miljöer. Detta ska göra att en applikation kan köras på exakt samma sätt utan kompabilitets problem oberoende av vilken dator/server den körs på, så länge Docker är installerat. Att applikationen kan köras oberoende av systemet gör att applikationen blir lättare att använda, utveckla, underhålla och driftsätta.



### Docker terminologi {#terminologi}

- **Image**: En image är typ ett exekverbart paket som innehåller allt som behövs för att köra applikationen, det inkluderar konfigurationsfiler, miljövariabler och bibliotek.
- **Dockerfile**: Fil som innehåller instruktionerna för att bygga en Docker image. Koden som används för att skapa en **Image**.
- **Build**: Skapar en image snapshot från Dockerfile.
- **Tag**: Version av en image. Varje image har ett tag namn.
- **Container**: Ett lättviktig program skapat från en specifik image version. Vi kan se det som att vi kallar en image en container när den exekveras.
- **DockerHub**: Image repository där vi kan hitta images. Typ GitHub för images.
- **Docker Daemon**: Körs på host systemet. Användare kan inte jobba direkt mot Docker daemon utan gör det via Docker klienter.
- **Docker Engine**: Skapar och kör Containers.
- **Docker Client**: Huvud interfacet för Docker.



### Installera Docker {#installera}

För att få en bättre förståelse för Docker behöver vi använda det och då måste vi installera det. Notera att det kan vara lite svårt med Docker i Windows 10 Home b.la., om ni har en annan miljö ni kan jobba på så rekommenderas det. Lösningen för tillfället är att köra Docker i VirtualBox på Windows 10 Home.

- [Installera virtualiseringsmiljön Docker](kunskap/installera-virtualiseringsmiljon-docker). 



### Öva på Docker {#ova}

Kolla på följande video för en kort introduktion till Docker och hur vi kan använda det.

[YOUTUBE src="6aBsjT5HoGY" caption="Docker Concepts Introduction"]

Om ni redan har läst kursen vlinux kan ni gå vidare till nästa steg. Annars jobba igenom hela följande guide för att lära er skapa egna images och containrar.

- [Docker](guide/docker/introduktion)

Om ni vill öva mer på Docker så finns det många [Docker övningar på Catacoda](https://katacoda.com/courses/docker).



### Docker i devops {#devops}

Docker är väldigt populärt inom devops världen av många anledningar och ni kan läsa varför i Dockers bloggserie **Docker and the Three Ways of DevOps**.

- [Part 1: The First Way – Systems Thinking](https://www.docker.com/blog/docker-three-ways-devops/)

- [Part 2: The Second Way – Amplify Feedback Loops](https://www.docker.com/blog/docker-three-ways-devops-2/)

- [Part 3: The Third Way – Culture of Continuous Experimentation and Learning](https://www.docker.com/blog/docker-three-ways-devops-3/)



## Skapa egen Docker image för produktion {#file_prod}

Nu när vi har lite kött på benen och vet vad Docker är och hur det fungerar ska ni skapa en egen Dockerfile för microblogen.

- Jobba igenom [Microblog med docker containers](kunskap/microblog_med_docker_containers) för att skapa dig en Dockerfile för produktion. Döp din Dockerfile till `Dockerfile_prod` och lägg den i mappen `docker`.

Efter att ni skapat er Dockerfile kan läsa två relevanta artiklar om docker användning.

- Vsupalov's review av [Docker Usage in 'The Flask Mega-Tutorial'](https://vsupalov.com/flask-megatutorial-review/).



### Databas i Docker {#db_docker}

Att köra sin databas i Docker har länge varit debatterat, många är emot men fler och fler börjar tycka att det är OK. Jag är för att köra databasen in Docker så länge man lägger data mappen som en volym så att datan inte skrivs över när vi startar om containern.

- Läsa lite om argumenten i [Should You Run Your Database in Docker?](https://vsupalov.com/database-in-docker/). 

MySQL sparar sin data i mappen `/var/lib/mysql` så när ni kör er databas container i produktion gör den mappen till en volym på host systemet. Så att datan i databasen inte försvinner när vi stänger ned containern.



## Skapa en Docker image för testning {#file_test}

Nu borde ni ha en image för produktions miljön, vi vill även ha en för vår utvecklings/testningsmiljö. Hur vår image ska bete sig skiljer mellan de olika miljöerna.

När vi kör docker i produktion vill vi att containern ska vara igång för evigt. När vi istället gör en image för testning vill vi starta upp en container, köra alla tester i den och sedan ska den stänga ner.

Vi vill inte behöva bygga om containern varje gång vi vill köra testerna. Som imagen för produktionsmiljön är byggd behöver vi bygga om den varje gång vi uppdaterar koden. Det tar för lång tid. Vi kan lösa det genom att inte kopiera in koden i containern när den byggs. Istället lägger vi mappen som koden ligger som en volym i containern. Då behöver bara containern innehålla miljön för att köra testerna. Detta gör att vi bara behöver skapa containern en gång och sen kan vi återanvända den när vi har ändrat i koden.

- Skapa en Dockerfile, döp den till `Dockerfile_test` och lägg den i mappen `docker`.
- I den ska ni inte kopiera in koden för testerna eller koden som testas. `app` och `tests` mapparna ska läggas som en volymer istället.
- När containern startar ska den validera koden och köra unit och integrations testerna. När det är klart ska containerna stängas ner av sig själv.

Om ni vill kan ni ändra så integrationstesterna körs mot MySQL i docker container istället för SQLite i minnet. Testerna kommer troligen köras långsammare men testerna blir mer värdefulla då de körs mot likadant system som körs i produktion. När man kör databasen i en container för testerna brukar man inte göra data mappen till en volym, i och med att vi inte bryr oss om persistent data för tester.

Kolla så att era Dockerfiler validerar med Hadolint. Det finns redan ett Make kommando, `make validate-docker`, som kör validering på `Dockerfile_prod` och `Dockerfile_test`.



## Spara konfiguration som kod {#konfig_kod}

En viktigt del av det praktiska inom devops är att spara konfiguration som kod och versionshantera den. Detta är för att undvika att tillfällen uppstår där det bara är specifika personer som vet hur man startar/kör/konfigurerar något. Allt ska finnas som kod och versionshanterat så alla kan göra det.

En typisk sån sak är att bygga/köra Docker images. Att bygga/starta en image behöver ofta någon slags konfiguration t.ex. vad ska vara volymer, miljövariabler eller vilken port som ska öppnas. Om detta inte finns som kod blir det svårt för någon annan än för den som skrev koden att göra det.

För Docker använder vi [docker-compose](https://docs.docker.com/compose/) i detta syftet. Om ni jobbade igenom hela docker guiden längre upp borde ni ha det installerat. Annars jobba igenom följande guide.

- [docker-compose](https://dbwebb.se/guide/docker/installera-compose).

Skapa filen `docker-compose.yml` i root mappen av repot. I den, lägg till en service för att köra test container och en som startar prod containern mot en MySQL container.

`docker-compose up test` ska starta test containern och köra alla tester.

`docker-compose up prod` ska starta en MySQL container och er prod container.

Uppdatera `make test` så det startar er test container och kör alla tester.



## CircleCI och Continuous Delivery {#circleci_cd}

Vi kan se Continuous Delivery som steget efter Continuous Integration. I CI har vi ett flöde där vi kör tester automatisk, nästa steg är när alla tester har blivit godkända. Då vill vi bygga vår applikation så att den finns tillgänglig för driftsättning med de senaste uppdateringarna. Vår applikation bygger vi genom att skapa en fungerande docker image. Läs en mer detaljerad förklaring av [Martin Fowler](https://martinfowler.com/bliki/ContinuousDelivery.html), ett av de stora namnen inom Microservices, Software Development och Continuous Integration/Delivery/Deployment. I nästa kursmoment ska vi ta det ett steg längre och uppnå Continuous Deployment, vilket lägger till att automatisk driftsätta applikationen efter vi testat och byggt den.
<!-- https://puppet.com/blog/continuous-delivery-vs-continuous-deployment-what-s-diff -->

Vi ska inte uppnå "riktigt" CD då vi inte har en staging miljö och vi borde testa koden mer rigoröst. Men vi jobbar med det vi har. Vi har redan ett CI flöde på CircleCi, nu ska ni bygga ut det med delivery steget. Om testerna går igenom ska ni bygga er produktions image och publicera den på DockerHub.

Om ni inte redan har ett, skapa först ett konto på [DockerHub](https://hub.docker.com/). Skapa sen ett nytt repo där ni kan ladda upp er produktions image. När ni gjort det testa ladda upp er första image manuellt. 

- [Skapa och hanter konto på DockerHub](https://dbwebb.se/guide/docker/skapa-och-hantera-konto).

Nu vill vi att er produktions image byggs och pushas till dockerhub automatiskt när ni pushar uppdateringar i er kod till GitHub. Vi gör så att detta sker i CircleCi. Läs följande artiklar för att se hur ni kan skriva er CircleCi config för att bygga och publicera er image till DockerHub. Tänk på att ni bara vill bygga och publicera en ny image om alla tester går igenom. Innan ni gör det kan ni installera CircleCi CLI för att slippa massa commits där CircleCi configen inte validerar.

- [Installera CircleCi CLI](kunskap/installera-circleci-cli).

- Ni som inte använder Cygwin kan även använda CircleCI för att [köra CircleCi jobb lokalt](https://circleci.com/docs/2.0/local-cli/#run-a-job-in-a-container-on-your-machine). Använd det och validate för att spara tid och slipp göra nya commits för att testa konfigurationen.

- [Using CircleCI workflows to replicate Docker Hub automated builds](https://circleci.com/blog/using-circleci-workflows-to-replicate-docker-hub-automated-builds/) 

Gör ett aktivt val mellan att publicera ny image för varje ny release eller vid varje commit!

Vi vill inte spara lösenord eller annan känslig information i kod så att det finns publikt på GitHub. Samtidigt behöver vi använda oss av t.ex. lösenord när vi kör saker i CircleCi. Känslig information kan vi spara som miljövariabler i CircleCi och sen använda i CircleCI flödet.

- Använda [miljövariabler i CircleCi](https://circleci.com/docs/2.0/env-vars/#setting-an-environment-variable-in-a-container).

<!-- Hur få exit kod? https://docs.docker.com/compose/reference/up/ --exit code from service, behövs den? -->



## Kör i produktion {#docker_prod}

Det sista steget är att köra er produktions container på er VM i Azure. Installera Docker på servern och starta up er microblog med docker-compose. Bygg inte containerna på servern utan använd den som byggts på CircleCi och laddas upp till DockerHub.

Ni ska inte använda supervisor längre. Vi använde supervisor för att se till att det hela tiden finns en Gunicorn process igång men det ansvaret flyttas över till Docker. Lägg till `restart: always` i er docker-compose fil.

Läs om vad Docker tycker om att använda [compose i produktion](https://docs.docker.com/compose/production/).



### Video {#video}

Det finns generellt kursmaterial i video form.


1. Kursen innehåller föreläsningar som spelas in och därefter läggs i spellistan "[devops streams ht20](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_MEDc_y12Zxdf3_zgb6YWy)".

1. I "[kursen devops](https://www.youtube.com/playlist?list=PLKtP9l5q3ce8s67TUj2qS85C4g1pbrx78)" hittar du alla videor som är kopplade till kursmomentet, de börjar på 2xx i namnet.



## Lästips {#lastips}

[Multistage builds](https://docs.docker.com/develop/develop-images/multistage-build/), för vår app är detta kanske inte nödvändigt men det är väldigt bra att känna till.

[Best practices](https://www.wintellect.com/security-best-practices-for-docker-images/) för Docker.

[Docker latest tag](https://vsupalov.com/docker-latest-tag/), ett annat hett ämne inom Docker är om man ska använda `latest` taggen för att köra images eller ej.

[Building Your Production Tech Stack for Docker Container Platform](https://dockercon2018.hubs.vidyard.com/watch/k3Cv676wmxAwYDxbvcgcgC), video från DockerCon 2018.



Uppgifter {#uppgifter}
-----------------------------------------------

Följande uppgifter skall utföras och resultatet skall redovisas.
<!-- nginx i docker med https https://medium.com/@pentacent/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71 -->

1. Två Dockerfile's i mappen `docker`, en för produktion som heter `Dockerfile_prod` och en som heter `Dockerfile_test`.

1. En docker-compose fil för att köra test och starta prod miljön.

1. Använd `make test` för att köra testerna och validerar kod i Docker. `validate-docker` funkar inte på CircleCi, om ni vill lägga till att validera era dockerfiler behöver ni använda en [docker orb](https://github.com/hadolint/hadolint/blob/master/docs/INTEGRATION.md#circleci)

1. CircleCi kör testerna, validering och bygger produktions image och pushar till DockerHub.

1. Försäkra dig om att du har pushat repot med din senaste kod och taggat din inlämning med version v2.0.0. Om du pushar kmom02 flera gånger kan du öka siffrorna efter 2:an.

1. Inkludera en länk till ditt GitHub repo och din webbsida (domännamn) i din inlämning på Canvas.



Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i texten:

1. Vad var din uppfattning av devops innan kursen började?

1. Har din uppfattning ändrats så här långt in i kursen?

1. Hur skulle du definiera devops?

1. Har du använt Docker förut? Gick det bra att använda det nu?

1. Valde du att bygga ny Docker image vid varje commit eller release? Varför?

1. Vad är Continuous Delivery?

1. Uppdaterade du deploy skripten med Docker?

1. Hur var storleken på kursmomentet? Vad tycker du om upplägget på kursmomentet?

1. Veckornas TIL?
