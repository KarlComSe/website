---
author: efo
category:
    - moln
revision:
    "2017-01-05": (C, mos) Notis om små bokstäver på filerna.
    "2016-01-20": (B, mos) Notis om att logg-filen är skyddad och inte kan öppnas via webbläsaren.
    "2015-06-24": (A, mos) Första utgåvan i samband med kursen linux.
...
Installera Debian och Apache i VirtualBox
==================================

Installera Debian som en server och kom igång och logga in på systemet med SSH.

<!--more-->



Förkunskaper {#forkunskaper}
-----------------------

Du har installerat en labbmiljö motsvarande "[Installera labbmiljön](vlinux/labbmiljo)". Du har jobbat igenom guiden "[Installera webbplatser med Apache Virtual Hosts](kunskap/installera-webbplatser-med-apache-name-based-virtual-hosts)" och guiden "[Kom igång med SSH-nycklar](guide/kom-igang-med-ssh/kom-igang-med-ssh-nycklar)".



Introduktion {#intro}
-----------------------

Se till att spara alla filer i en katalog på datorn. De används för att redovisa uppgiften.

Skapa en fil, `log.txt`, och lägg den i katalogen ovan. I kraven nedan kallas denna fil för *loggen*. I filen skall du föra noteringar för din egen del. Det kan vara bra som minnesanteckningar, så går det enklare nästa gång du installerar ett liknande system.

En bra sak är att logga varje kommando du kör, så får du en logg som du kan titta tillbaka på. Det är lätt att glömma alla nya kommandon, så en logg för minnet blir bra.

Det finns ett par saker som du måste skriva i filen `log.txt`, det står isåfall i kraven nedan. Men i övrigt så skriver du anteckningar som du vill.



Krav {#krav}
-----------------------

1. Installera Debian. Notera i loggen vilket namn du ger servern.

1. Logga in på din server. Notera i loggen vilken ip-adress servern har.

1. På servern, kör kommandot `uname -a`, notera svaret i loggen.

1. Öppna en terminal på din arbetsstation. Använd SSH för att logga in på servern. När du är inloggad så kör du kommandot `cowsay` med en trevlig hälsningsfras. Ta en skärmdump av terminalfönstret som visar resultatet. Spara bilden i formatet PNG och lägg filen i samma katalog som loggfilen, döp den till `ssh.png` (använd små bokstäver i filnamnet, inte STORA).

1. Skapa en Apache Virtual Host `me.linux.se`. Spara en kopia av config-filen `me.linux.se.conf` i din katalog. Kontrollera att du kommer åt webbplatsen med din webbläsare.

1. Öppna en terminal i din VM, använd `lynx` för att öppna din nyligen skapade webbplats. Skriv kommandot du använder i loggen.

1. Ta en skärmdump på terminalen som visar när du använder `lynx` för att komma åt webbplatsen. Spara den som `dump.png`. Spara bilden i formatet .png och använd små bokstäver i filnamnet.

1. Lägg alla filer (`log.txt`, `ssh.png`, `dump.png` och `me.linux.se.conf`) som en del av din inlämning i Canvas.



Tips från coachen {#tips}
-----------------------

Stressa inte. Kör det ihop sig så är det en bra taktik att börja om från början och göra om. Det går snabbare andra gången, och ännu snabbare tredje gången.

Lycka till och hojta till i forumet om du behöver hjälp!
