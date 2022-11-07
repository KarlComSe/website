---
views:
    flash:
        region: flash
        template: default/image
        data:
            src: "image/vteam/logo.png"
author: mos
revision:
    "2022-10-24": "(B, mos) Länk till domänbeskrivning."
    "2022-10-10": "(A, mos) Första utgåva inför kursstart HT2022."
...
Veckoplan med kursveckor - vad händer och vad göra?
=========================

Detta dokument uppdateras löpande under kursen, som minnesnoteringar för vad som händer i varje kursvecka.

Varje kursvecka förekommer ett eller flera fokusområden som presenteras från lärarteamet med föreläsningar och/eller artiklar. Dessa fokusområden skall sedan diskuteras och hanteras i grupperna och införlivas i gruppens arbete.

<!--
TODO

* Maila refgruppen och be om tips - vad säga till studenterna om vad som är viktigt när man jobbar i grupp och vilka arbetssätt som normalt förekommer ute.

LINKS

* vteam streams https://www.youtube.com/playlist?list=PLKtP9l5q3ce_wXroqbxvzSNBzi2Yy8ULF
* vteam How To https://www.youtube.com/playlist?list=PLKtP9l5q3ce9BUGisXHdP8dueMoaXyQ71

* Förra årets streams:
https://www.youtube.com/playlist?list=PLKtP9l5q3ce9JglLprvPbXklQiAC_Jizu

-->



Förbered inför kursen {#prepare}
-------------------------

Skaffa dig en grupp genom att till exempel annonsera att du söker en grupp i kursens chattkanal eller prata med dina studiekompisar.

Läs igenom bakgrunden till projektet i dokumentet "[Elsparkcyklar bakgrundsanalys](https://drive.google.com/file/d/19qRnYcCYRRba3ePd5fbuxtMf3B04qmfs/view?usp=sharing)" för att skaffa dig kunskap om den domän där du skall verka i.



Vecka 01 (v44): Kund och uppdrag {#w01}
-------------------------

<!--
TODO 

* Kursintroduktion och genomgång av domänen och kravspecen, använd materialet på Canvas och dbebb.
* Presentation av systemarkitekturer.
* Genomgång av uppgiften SDS.
* Gör en template till SDS:en?

* Frågor till referensgruppen från studenterna.
-->

Kursen startar och projektet presenteras tillsammans med kursens upplägg. Kundens kravbild gås igenom. Första uppgiften gås igenom, det handlar om förutsättningar för att skapa en översikt av systemet via en System Design Specification (SDS). Vi pratar om olika typer av arkitekturer när man bygger ett större system.

Innan veckan är slut skall alla finnas i en grupp. Gruppstorleken är 4 studenter.

**Presentation**

* [System Design Specification (SDS) (slides)](https://dbwebb-se.github.io/pattern/lecture/L01-system-design-specification/slide.html)

**Material**

Följande material är viktiga styrdokument att sätta sig in i.

1. "[Elsparkcyklar bakgrundsanalys](https://drive.google.com/file/d/19qRnYcCYRRba3ePd5fbuxtMf3B04qmfs/view?usp=sharing)"
1. [Kravspecifikation](https://docs.google.com/document/d/1zWksQNmkXJgM7Q66k3-mgcxrexO6eF9xqd0Z632BwlU/edit?usp=sharing)
1. [Tips, trix och förtydliganden](./../tips-trix-och-fortydliganden)

**Resurser**

Följande läsresurser är relevanta denna veckan.

Rörande arkitektur.

1. [Software architecture patterns - Take a deep dive into several common software architecture patterns](https://www.oreilly.com/content/software-architecture-patterns/)
    1. [The top 5 software architecture patterns: How to make the right choice (shorter article on the same matter)](https://techbeacon.com/app-dev-testing/top-5-software-architecture-patterns-how-make-right-choice)
1. [The Big Ball of Mud and Other Architectural Disasters](https://blog.codinghorror.com/the-big-ball-of-mud-and-other-architectural-disasters/)
    1. [Big Ball of Mud (original paper)](http://www.laputan.org/mud/mud.html)
    1. [Why Software Becomes a Big Ball of Mud (yet another (short) article on the matter)](https://pressupinc.com/blog/2015/04/why-software-becomes-a-big-ball-of-mud/)
1. [What UML diagram should I use to show a platform's architecture? (TLDR; "make it look good")](https://softwareengineering.stackexchange.com/questions/198178/what-uml-diagram-should-i-use-to-show-a-platforms-architecture)
1. Paper "[Architectural Blueprints—The 4+1 View Model of Software Architecture](https://www.cs.ubc.ca/~gregor/teaching/papers/4+1view-architecture.pdf)" showing examples on how to draw 4+1 architecture blueprints.

Rörande arbetsmetoder.

1. [Vad är ett stand-up meeting?](https://en.wikipedia.org/wiki/Stand-up_meeting) Vilka frågor känns relevanta att svara på ett stand-up?
1. [Vilken är din roll i gruppen?](https://www.youtube.com/watch?v=7KSCvPwNrzE&list=PLKtP9l5q3ce9BUGisXHdP8dueMoaXyQ71) Emil lyfter frågan om hur en grupp organiserar sig och vilken roll man tar på sig.

**Assignment**

* Börja jobba med [uppgiften SDS:en](./../assignment/system-design-specification).



Vecka 02 (v45): Fokus Serversidan {#w02}
-------------------------

<!--
TODO

1. Utgå från architecture.svg och en översikt av systemet/arkitekturen [architecture.svg](https://github.com/dbwebb-se/pattern/blob/main/docs/lecture/L02-RESTful-API/architecture.svg), [web](https://dbwebb-se.github.io/pattern/lecture/L02-RESTful-API/architecture.svg)

    * Utgå från bilden och börja skissa på backenden
    * Rita och skissa, prata och diskutera
    * MVC, web, rest, db, sas, möjliga artifekter, programmeringskod, ramverk, språk

2. Designa ett REST API.

    * I lektionen skissade vi på en [REST API matris](https://docs.google.com/spreadsheets/d/1V_2KmGhWYd4qShBpHRBNepor11cSS6YxFjAHmlPEtJ4/edit?usp=sharing) som en variant av hur man kan skissa och designa sitt REST API. På ett sätt är detta jämförbart med hur man skissar och designar en databas med ER-modellering.
    * Hur dokumentera ett REST API? [REM server](https://rem.dbwebb.se/) som exempel.

3. Hur jobba med Git repon (GitHub eller GitLab) när man jobbar i grupp?

    * [Understanding the GitHub flow](https://guides.github.com/introduction/flow/)
    * [Introduction to GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)

4. Vad innebär "högpresterande team" och vad är "bike shedding"?

    * [Tuckman's stages of group development](https://en.wikipedia.org/wiki/Tuckman%27s_stages_of_group_development)
    * [High-performance teams](https://en.wikipedia.org/wiki/High-performance_teams)
    * [Bike shedding / Law of triviality](https://en.wikipedia.org/wiki/Law_of_triviality)

5. Tekniska studier och rapporter för att lära sig och sprida kunskap.

    * https://dbwebb.se/kurser/vteam-v1/tips-trix-och-fortydliganden#tech
-->

Jobba vidare med SDS för att bryta ned och förstå systemet och dess delar. Fokus på serversidan av projektet.

**Presentation**

Vi träffas och pratar som saker som hjälper oss framåt.

1. Jobba med arkitekturen och backenden samt olika teknikval
1. Designa och dokumentera ett REST API
1. GitHub/GitLab flow
1. Effektiva och högpresterande team
1. Tekniska studier och rapporter för att lära sig och sprida kunskap.
    * Någon som är sugen på en teknisk studie om Docker med många containrar?

**Resurser**

Följande läsresurser är relevanta denna veckan.

Följande artikelserie tar dig igenom hur man kan tänka när man designar ett REST API. Du får också stöd för hur du kan designa ditt API med en matris som lite kan liknas vid hur vi designade databasen med ER-modellering.

1. [How to design a RESTful API architecture from a human-language spec (part 1)](https://www.oreilly.com/content/how-to-design-a-restful-api-architecture-from-a-human-language-spec/)
1. [How a RESTful API server reacts to requests (part 2)](https://www.oreilly.com/content/how-a-restful-api-server-reacts-to-requests/)
1. [How a RESTful API represents resources (part 3)](https://www.oreilly.com/content/how-a-restful-api-represents-resources/)

Här är en [REM server](https://rem.dbwebb.se/) som visar ett exempel på hur en API:et till en REST server kan se ut och som kan användas för test. Använd en REST klient likt [ARC](https://advancedrestclient.com/) för att testa API:et.

Hur jobba med Git repon (GitHub eller GitLab) när man jobbar i grupp?

* [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
* [Understanding the GitHub flow](https://guides.github.com/introduction/flow/)
* [Introduction to GitLab Flow](https://docs.gitlab.com/ee/topics/gitlab_flow.html)

Vad innebär "högpresterande team" och vad är "bike shedding"?

* [Tuckman's stages of group development](https://en.wikipedia.org/wiki/Tuckman%27s_stages_of_group_development)
* [High-performance teams](https://en.wikipedia.org/wiki/High-performance_teams)
* [Bike shedding / Law of triviality](https://en.wikipedia.org/wiki/Law_of_triviality)

Tekniska rapporter för att göra små korta utredningar och presentera resultat.

* [Exempel på tekniska studier och rapporter](https://dbwebb.se/kurser/vteam-v1/tips-trix-och-fortydliganden#tech)



Vecka 03 (v46): Fokus Klientsidan {#w03}
-------------------------

<!--
TODO

* Tekniker för klientsidan
* Riskanalys (eller flytta till nästa vecka)
* Effektivetet 10
1. Docker med flera containrar, skapa en teknisk rapport om det.

-->

<!--
Om det är någon som vill hoppa på frontend delen men inte har tillgång till någon server/api hämtning av datan än, så tipsar jag på npm packetet json-server https://www.npmjs.com/package/json-server
1) npm i json-server
2) skapa en json fil med data som tex bike.json
{
  "bikes": [
    { "id": 1, "cords": [200, 210] }
  ]
}
3) json-server --watch bike.json
4) profit
Nu kan ni fetcha data från http://localhost:5000/bikes 
-->

Jobba med SDS. Fokus på klientsidan av projektet. Gräv djupare in i serversidan.

<!--
Hur ser industrin på att organisera sig i team och grupper?

* [Martin Mazur - Dagens Industri IT & Strategy](https://www.linkedin.com/feed/update/urn:li:activity:6861311477781970944/)

Vilka krav har industrin på nya studenter?

* [Jane Strandberg, teamleader och chef, Prisjakt](https://gist.github.com/mosbth/76a4d7a503e45692d28c4c0dcd029703)
* Input från en annan XXX som jobbar på ett av Sveriges största IT-bolag

[Presentationen från måndagen (lite arkitektur och lite om teams)](https://dbwebb-se.github.io/pattern/lecture/L03-seminar/slide.html)

Torsdagen i vecka 2 hade vi en session om riskanalys av projektet som också spelades in.

* [Riskanalysdokumentet](https://docs.google.com/spreadsheets/d/1jqmyl1bKGc7La81MfwGVY0JqVPmopM0oG9s8-gCGEkc/edit?usp=sharing)
* [Zoom-sessionen om riskerna](https://youtu.be/r-c7ETb80M0)

-->



Vecka 04 (v47): SDS Klar  {#w04}
-------------------------

Leverans av SDS.

<!--
* Individuell reflektion över arbetet så här långt samt se vilken plats man själv tar i projektet.
    * Fundera på om det är något man vill ändra för resten av projektet.
* Jobba med små tekniska studier och dela kunskap
-->


<!--
Vad vill näringslivet att vi skall kunna när vi kommer ut? Vilket behov upplever de att de har av programmerare och vilka krav ställer de på nyanställda? Mikael har pratat med gamla studenter och samlat ihop vad de anser vara viktigt.

[Teknisk studie i OAuth](https://github.com/mosbth/oauth-tec-study/blob/main/OAuth_Technical_Study.md). Hur sprider man denna typen av kunskap i en arbetsgrupp och mellan grupper?

Automatisera tester och byggen med byggtjänster och tjänster för kodkvalitet.

(Docker, docker-compose, en miljö för test och utveckling.)

**Torsdag**

Denna veckan blir det ingen Q&A session, istället finns det två videor/föreläsningar att titta på och en liten mini-uppgift som gäller att besvara frågan.

> "Vad innebär "vacker kod" och är det något vi kan applicera i vårt projekt?"

1. Video 1 "[The concept of Good and Clean Code](https://www.youtube.com/watch?v=drkATTaqEiw)"
1. Video 2 "[Software philosophies and principles](https://www.youtube.com/watch?v=xLCHREF5I-I)"

Mini-uppgiften löser du i 'Reflektera över "Good and Clean Code"'.
-->



Vecka 05 (v48): Implementera {#w05}
-------------------------

Påbörja implementationsfasen av projektet och implementera systemet enligt er SDS.

<!--
Vi hade en kort generell avstämning av läget, allt verkar så här långt "se bra ut". Det dyker inte upp så många frågor.

Man kan nu boka in en tid för att leverera i december och vi fortsätter med korta träffar på måndagar och torsdagar inleds med en timme öppet hus för frågor och därefter kan man boka in gruppvis diskussioner.

(Övriga diskussioner kring implementationen av systemet, eventuellt justeringar av kraven.)

(Hur simulerar man ett system i drift?)

https://dbwebb.se/kunskap/gps-och-karta
-->



Vecka 06 (v49): Teknikval {#w06}
-------------------------

Lämna in de teknikval ni gjort för projektet och berätta kort om hur ni kommer att implementera systemet.



Vecka 07 (v50): Implementera projektet {#w07}
-------------------------

Jobba med implementationen av projektet och se till att kontinuerligt integrera teamets arbete i en helhet.

Första möjligheten att göra en leverans av systemet.



Vecka 08 (v51): Implementera projektet {#w08}
-------------------------


Vecka 09 (v52): Implementera projektet {#w09}
-------------------------


Vecka 10 (v01): Förbered inför leverans {#w10}
-------------------------

Jobba med projektet och förbered inför leveransen. Genomför en egenkontroll i form av en avstämning inför slutleveransen, vad skall finnas med och hur skall det leveraras, dokumenteras, presenteras och testköras?



Vecka 11 (v02): Leverans och redovisning {#w11}
-------------------------

Gruppen levererar systemet och presenterar arbetet och demonstrerar att systemet fungerar.

Avslutningsvis skrivs en slutrapport från gruppens projektarbetet. Slutrapporten innehåller även en erfarenhetsrapport med lärdomar.

Varje deltagare skriver också en avslutande summering av sina egna erfarenheter och lärdomar av gruppens arbete och kursens utformning.

<!-- Vad gjorde vi bra och vad kan vi göra bättre nästa gång samt fem viktiga tips (tekniska tips och grupptips) till grupperna som går detta projekt nästa år -->



<!--
* Påvisa goda kunskaper i att designa större applikationer och system inom webbteknologier genom att skriftligen beskriva och sammanfatta arkitekturen för systemet.
* Påvisa goda kunskaper att jobba i en grupp och aktivt delta i gruppens löpande arbete samt inse olika kriterier som kan ge en hälsosam grupp.

* Utifrån en större kravspecifikation kunna designa, utveckla och leverera ett komplett och fungerande system där möjlighet till olika prioriteringar medges.
* Visa mycket god förmåga att skapa kod som kan betraktas som ”god och snygg kod” genom att använda filosofier, tester och analysverktyg som hjälper att skapa en bild av det som kan vara "god kod".

* Självständigt och i grupp kritiskt kunna utvärdera och analysera sin tekniska lösning och de
prioriteringar som ledde fram till den.
* Självständigt och i grupp reflektera över de byggstenar som gör en god och hälsosam grupp och
grupparbete.
-->