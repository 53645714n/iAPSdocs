# Wie man den ersten PR (Pull Request) macht

Es kann sein, dass dir irgendwann vorgeschlagen wird, einen PR zu machen. PR, die Abkürzung für Pull-Request, ist eine Möglichkeit wie man Quellcode oder - wie in diesem Fall - Dokumentationen auf GitHub ergänzen oder ändern kann. Es ist eigentlich nicht allzu schwer und eine gute Möglichkeit, einen Beitrag zu leisten. Diese Dokumentation gibt es, weil Leute wie du PRs gemacht haben. Mach dir keine Sorgen einen Fehler zu machen oder irgendwie die falschen Dokumente zu bearbeiten. Es wird immer Korrektur gelesen, bevor Änderungen in die "finale" AndroidAPS Dokumentation integriert werden. Du kannst das Original nicht zerstören, wenn du beim PR etwas falsch machst. Die allgemeine Vorgehensweise ist:

* Mache Änderungen und Verbesserungen am Code oder der Dokumentation, indem du das bestehende Dokument veränderst.
* Vergewissere dich, dass die Änderungen gut aussehen.
* Füge Notizen hinzu, damit andere die Änderungen verstehen können.
* Erstelle einen Pull-Request, durch den die Administratoren aufgefordert werden deine Änderungen zu verwenden.
* Sie werden sich das anschauen und entweder (1) deine Änderungen übernehmen (2) deine Änderungen kommentieren oder (3) ein neues Dokument mit deinen Änderungen erstellen.

(Randbemerkung: Wenn Du ein visueller Lerner bist, gibt es [hier](https://youtu.be/4b6tsL0_kzg) ein YouTube Video, das den PR-Prozess darstellt.)

In unserem Beispiel nehmen wir nun eine Änderung an der AndroidAPS-Dokumentation vor. Dies muss nicht in einer Linux-Umgebung durchgeführt werden. Es kann auf jedem Windows-PC, Mac, etc. erfolgen. (jedem Computer mit Internet-Zugang).

1. Gehe zu https://github.com/openaps/AndroidAPSdocs und klicke auf "Fork" oben rechts, um deine eigene Kopie des Repositories (=Quell-Code) zu machen. ![Fork repo](./images/PR0.png)
2. Gehe zu http://androidaps.readthedocs.io/en/latest/Getting-Started/Safety-first.html oder ähnliches und navigiere zu der Seite, die du bearbeiten möchtest. Klicke auf die Black-Box unten links in der Seite mit dem grünen Wort "v: newest" oder ähnliches. In dem Fenster das nun erscheint klicke auf das Wort "edit", um es in Github zu editieren.   
    ![edit doc](./images/PR1.png) Oder du klickst auf den "Edit in Github"-Link in der oberen rechten Ecke und klickst dann auf das Bleistift-Symbol das in der oberen Leiste der Seite erscheint, um diese zu editieren. ![RTD io](./images/PR2.png)
3. Beide Optionen in Schritt 2 führen dazu, dass ein neuer Branch in DEINEM kopierten Repository erstellt wird, wo die Änderungen gespeichert werden sollen. Editiere die Datei. ![Edit branch](./images/PR3.png)
4. Du arbeitest im "<>Edit file" Reiter. Wechsle zum "Preview changes" Reiter, um auf die Vorschau einen Blick zu werfen, damit alles was du geändert hast so aussieht wie du es wolltest (Rechtschreibfehler prüfen). Wenn du etwas entdeckst, das ausgebessert werden muss, wechsle wieder zum edit Reiter, um die Ausbesserungen vorzunehmen. ![preview mode](./images/PR5.png)
5. Wenn du mit deinen Änderungen fertig bist, scrolle zum Seitenende. In der Box am Seitende solltest du deine Kommentare im Textfeld namens "Add an optional extended description..." einfügen. Der Standardtitel beinhaltet den Dateinamen. Versuche einen Satz dazu zu schreiben, **warum** du etwas geändert hast. Die Angabe des Grundes hilft den Admins zu verstehen, was du mit deinem PR bezweckst. ![commit comments](./images/PR4.png)
6. Klicke auf den grünen "Propose file changes" (Änderungen vorschlagen) oder "Commit changes" (Änderungen integrieren) Button. Auf der Seite, die dann erscheint, klicke auf "Create Pull Request" und auf der dann erscheinenden Seite klicke auf "Create Pull Request". ![create pull request](./images/PR6.png)
7. Das war der letzte Schritt zur Erstellung eines pull requests, PR. GitHub ordnet dem PR eine Nummer, die du nach dem Titel findest, zu und einen Hashtag. Rufe diese Seite wieder auf, um Feedback zu erhalten (oder du erhältst automatisch E-Mail Benachrichtigungen über Aktivitäten bei deinem PR, wenn du Github entsprechend konfiguriert hast). Die Änderung wird nun in einer Liste von PR's aufgeführt, die das Team überprüfen wird; es wird gegebenenfalls Rückmeldungen dazu geben, bevor die Änderung in die Hauptdokumentation für AndroidAPS einfliesst! Wenn du den Fortschritt des PR überprüfen willst, kannst du auf das Logo mit der Glocke in der oberen rechten Ecke deines GitHub-Kontos klicken, wo du dann alle deine PRs siehst. ![PR tracking](./images/PR7.png)

Gratulation, du hast deinen ersten Beitrag geleistet!

PS: dein Fork und Branch befinden sich nach wie vor auf deinem persönlichen GitHub Konto. Nachdem du die Benachrichtigung erhalten hast, dass dein PR integriert wurde, kannst du deinen Branch löschen, wenn du damit fertig bist (der Benachrichtigungsbereich in Schritt 8 stellt dir einen Link zur Verfügung, um den Branch zu löschen, wenn er geschlossen oder integriert wurde). Künftige Änderungen werden immer mit einer aktuellen Version des AndroidAPS Repositories beginnen, wenn du diese Vorgehensweise verwendest. Wenn du eine andere Methode verwendest, um einen PR zu starten (z.B. du fängst mit einem lokalen Fork des Master Branches an), musst du sicherstellen, dass dein Repository aktuell ist, indem du erst ein "compare" ausführst und damit alle Updates integrierst, die seit dem letzten Update deines Forks stattgefunden haben. Da häufig vergessen wird, die eigenen Repositories auf dem aktuellen Stand zu halten, empfehlen wir, den PR Prozess wie oben beschrieben zu verwenden, bis du dich mit der Ausführung von "compares" vertraut gemacht hast.

### Advanced tips for adding internal links

If you want to set an internal link within the AndroidAPS documentation, please only use **relative links**. Only this will make the link work in the other languages as well.

In files with .md ending:

* [\[text\](../Usage/Test.md)](../Usage/Test.md) will set a hyperlink one directory down from where you are and then into the subdirectory /Usage. Ending of the target file must be .md or .rst (not .html)
* [\[text\](/Usage/Test.md)](/Usage/Test.md) will set a hyperlink from where you are into /Usage. Ending of the target file must be .md or .rst (not .html)

In files with .rst ending:

* `Text <../Usage/Test.md>`_ will set a hyperlink one directory down from where you are and then into the subdirectory /Usage. Ending of the target file must be .md or .rst (not .html)
* `Text <./Usage/Test.md>`_ will set a hyperlink from where you are into /Usage. Ending of the target file must be .md or .rst (not .html)

### Advanced tips for adding multiple images to documentation

If you are planning to make a lot of edits, including adding images to help illustrate parts of the documentation (thank you!), you may want to take the following approach:

* As you go and save screenshots, rename the screenshots to a descriptive name - but try not to use spaces as that confuses Github. Instead, use underscores. I.e. Example_batch_images_upload.png rather than "Example batch images upload.png".

* You can upload images in batches easily by:
    
    1. Navigate to the images folder (https://github.com/openaps/AndroidAPSdocs/tree/master/docs/EN/images - but make sure you are in your fork/copy of the docs Images folder to be able to do this (replace "openaps" in the URL with your github username)).
    
    2. Click in the upper right corner where it says "Upload files"
    
    3. Drag and drop your images into the screen
    
    4. Commit these to your branch
    
    5. Now, you can look for the URL/relative path of each file (example, you can see [this individual image has its own URL and path](https://github.com/openaps/docs/blob/master/docs/EN/images/Example_batch_images_upload.png) and use that to refer to when adding images into a page in the documentation.
    
    6. To see examples of how to add the images, you can look at the "raw" code of a page to see an example from a page that already has the images embedded successfully. The main thing is to have a plain text description, followed by a link with a relative path to the image, like this: `![Example of uploading images in batches](../images/Example_batch_images_upload.png)`
    
    (That code is exactly how the image below is embedded to be displayed.)

![Example of uploading images in batches](./images/Example_batch_images_upload.png)

7. Nachdem du Bilder hinzugefügt oder Veränderungen vorgenommen hast, kannst du einen PR auf das master branch von AndroidAPSdocs machen.