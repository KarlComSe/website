---
author:
    - lew
revision:
    "2022-04-11": (A, lew) Ny inför HT22.
...
Kmom02: Dockerfile och Bash
==================================

[WARNING]
Kursen uppdateras inför HT22. Är "gula rutan" borta är det fritt fram att börja.
[/WARNING]

Nu har vi fått Dockermiljön på plats och vi vet hur vi startar en container samt hur vi navigerar i den. Vi ska nu titta på hur vi kan skapa en egen image utifrån en så kallad Dockerfile så vi slipper installera om allt varje gång vi stänger ner containern. Vi ska också lära oss hur vi kan skapa bashscript som vi exekverar i containern.


<!--more-->

[FIGURE src=/image/vlinux/bashlogo.png caption="Bash."]




<small><i>(Detta är instruktionen för kursmomentet och omfattar det som skall göras inom ramen för kursmomentet. Momentet omfattar cirka **20 studietimmar** inklusive läsning, arbete med övningar och uppgifter, felsökning, problemlösning, redovisning och eftertanke. Läs igenom hela kursmomentet innan du börjar jobba. Om möjligt -- planera och prioritera var du vill lägga tiden.)</i></small>



Läsanvisningar  {#lasanvisningar}
---------------------------------

*(ca: 4-10 studietimmar)*


### Kurslitteratur  {#kurslitteratur}

Läs följande:

1. [The Linux Command Line](kunskap/boken-the-linux-command-line)
    * Kapitel 1-4, repetera grundläggande kommandon

<!-- I referenslitteraturen, är följande kapitel relevanta. -->

<!-- 1. [The Debian Administrator's Handbook](kunskap/boken-the-debian-administrator-s-handbook).
    * Ch 6: Maintenance and Updates: The APT Tools (speciellt om `apt-get`, annars översiktligt)
    * Ch 7: Solving Problems and Finding Relevant Information (översiktligt) -->



### Artiklar {#artiklar}

1. Boken "The Linux Command Line" har en webbplats där det finns [ett stycke med fokus på att lära sig terminalen](http://linuxcommand.org/lc3_learning_the_shell.php). Ta det som ett lättläst komplement till boken.



###  TBD!! Video  {#video}

<!-- Titta på följande:

1. Till kursen finns en videoserie, "[vlinux](https://www.youtube.com/playlist?list=PLKtP9l5q3ce_oeXQlDtKv51tVM4Y8UtkF)", kika på de videor som börjar på 02.
 -->


Övningar & Uppgifter  {#ovningar_uppgifter}
-------------------------------------------

*(ca: 6-10 studietimmar)*



### Övningar {#ovningar}

Genomför följande övningar.

1. Jobba igenom artikeln ["Skapa Bash-skript med options, command och arguments"](kunskap/skapa-bash-skript-med-options-command-och-arguments). Den ger dig en struktur till hur du kan skapa Bash-skript.

1. Läs stycket om verktyget "grep" i artikeln ["Text processering"](kunskap/text-processering#grep).

1. Kika i guiden [kom igång med Bash](guide/kom-igang-med-bash), där du hittar beskrivningar om de vanligaste konstruktionerna.

<!-- 1. Jobba igenom guiden om "[Apache Name-based Virtual Hosts](guide/unix-tools/apache)".

1. Jobba igenom guiden "[Kom igång med SSH-nycklar](guide/unix-tools/kom-igang-med-ssh-nycklar)".

1. Jobba igenom guiden om "[rsync](guide/unix-tools/rsync)".

1. Jobba igenom guiden om "[tmux](guide/unix-tools/tmux)".
 -->




### Uppgifter {#uppgifter}

Dessa uppgifter skall utföras och redovisas.

1. Gör uppgiften [Lab 1](uppgift/linux-lab-1-introduktion-till-bash) för att träna upp grundläggande färdigheter i bash och hantering av filsystem.

1. Gör uppgiften "[Bash-script med argument options](uppgift/ett-bash-script-med-options-command-arguments)". Spara arbetet i mappen `kmom02/ex1`.

1. Gör uppgiften "[Skapa Docker image](uppgift/skapa-docker-image)". Du fortsätter arbeta i mappen `kmom02/ex2`.

<!-- 1. Gör uppgiften "[Skapa en webbplats på en Apache Virtual Host](uppgift/skapa-en-webbplats-pa-en-apache-virtual-host)". -->

1. Lägg till redovisningstexten i din me-sida.

<!--
1. Gör uppgiften "[Strukturera filer, kataloger och rättigheter i en webbplats](uppgift/strukturera-filer-kataloger-och-rattigheter-i-en-webbplats)".
-->

### Testa din inlämning {#test}

Du kan köra vissa tester på din inlämning och se om de delarna uppfyller kraven. Rättningen kommer endast genomföras om testerna går igenom.

```console
$ dbwebb test kmom02
```


Resultat & Redovisning  {#resultat_redovisning}
-----------------------------------------------

*(ca: 1-2 studietimmar)*

Läs [instruktionen om hur du skall redovisa](./../redovisa).

Se till att följande frågor besvaras i redovisningstexten.

* Är detta din första bekantskap med skriptprogrammering i Bash?
* Berätta om din uppfattning om Bash som programmeringsmiljö, relatera till andra programspråk du kan.
* Vilka möjligheter/utmaningar ser du med denna typen av skriptprogrammering?
* Var det något som var extra svårt eller utmanande i uppgifterna?
* Reflektera över hur du känner inför ett Unix-liknande operativsystem så här långt?
