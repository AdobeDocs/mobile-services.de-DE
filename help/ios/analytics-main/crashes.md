---
description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-description: Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.
seo-title: App-Abstürze verfolgen
solution: Marketing Cloud, Analytics
title: App-Abstürze verfolgen
topic: Entwickler und Implementierung
uuid: 4 f 81988 b -198 a -4 ba 9-ad 53-78 af 90 e 43856
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Nachverfolgen von App-Abstürzen {#track-app-crashes}

Mithilfe dieser Informationen können Sie ermitteln, wie Abstürze verfolgt werden und wie Sie am besten mit fälschlich gemeldeten Abstürzen umgehen.

>[!IMPORTANT]
>
>Sie sollten auf die ios SDK Version 4.8.6 aktualisieren, die wichtige Änderungen enthält, die verhindern, dass falsche Abstürze gemeldet werden.

## Wann meldet Adobe einen Absturz?

Wenn Ihre Anwendung beendet wird, ohne dass sie zunächst in den Hintergrund versetzt wurde, meldet das SDK beim nächsten Start Ihrer App einen Absturz.

## Wie funktionieren Absturzberichte?

iOS verwendet Systembenachrichtigungen, die Entwicklern ermöglichen, unterschiedliche Status und Ereignisse im Anwendungslebenszyklus zu verfolgen und darauf zu reagieren.

Das Adobe Mobile iOS-SDK verfügt über einen Benachrichtigungs-Handler, der auf die Benachrichtigung `UIApplicationDidEnterBackgroundNotification` reagiert. In diesem Code wird ein Wert festgelegt, der angibt, dass der Benutzer die App in den Hintergrund versetzt hat. Wenn bei einem nachfolgenden Start dieser Wert nicht gefunden werden kann, wird ein Absturz gemeldet.

## Warum werden Abstürze von Adobe auf diese Weise gemessen?

Dieser Ansatz, Abstürze zu messen, bietet eine allgemeine Antwort auf die Frage „*Hat der Benutzer meine App mit Absicht beendet?*“

Von Unternehmen wie Apteligent (hieß zuvor Crittercism) bereitgestellte Absturzberichtsbibliotheken verwenden einen globalen `NSException`-Handler, um ausführlichere Absturzberichte bereitzustellen. Ihre App darf nicht mehr als einen dieser Handlertypen aufweisen. Adobe hat sich im Bewusstsein, dass unsere Kunden möglicherweise andere Absturzberichtsanbieter verwenden, dazu entschieden, keinen globalen `NSException`-Handler zu implementieren, der dazu dient, Build-Fehler zu verhindern.

## Wie kann es passieren, dass fälschlicherweise ein Absturz gemeldet wird?

Die folgenden Szenarien sind dafür bekannt, dass in ihnen fälschlicherweise ein Absturz verursacht wird, der vom SDK gemeldet wird:

* Wenn Sie mittels Xcode debuggen, wird ein Absturz ausgelöst, wenn Sie versuchen, die App erneut auszuführen, während sie sich im Vordergrund befindet.

   >[!TIP]
   >
   >Sie können in diesem Szenario einen Absturz vermeiden, indem Sie die App hintergrundig machen, bevor Sie die App erneut aus Xcode starten.

* If your app is in the background and sends Analytics hits through a call other than `trackActionFromBackground`, `trackLocation`, or `trackBeacon`, and the app is terminated (manually or by the OS) while in the background, and the next launch will be a crash.

   >[!TIP]
   >
   >Background activity that occurs beyond the `lifecycleTimeout` threshold might also result in an additional false launch.

* Wenn Ihre App im Zuge eines Hintergrundabrufs, Standortupdates usw. im Hintergrund ausgeführt und durch das Betriebssystem beendet wird, ohne jemals in den Vordergrund versetzt zu werden, führt der nächste Start (im Hinter- oder Vordergrund) zu einem Absturz.
* Wenn Sie das „pause“-Kennzeichen von Adobe in `NSUserDefaults` programmgesteuert löschen, während sich die App im Hintergrund befindet, führt der nächste Start oder die nächste Fortsetzung zu einem Absturz.

## Wie kann ich verhindern, dass falsche Abstürze gemeldet werden?

Mithilfe der folgenden Vorgehensweisen kann verhindert werden, dass falsche Abstürze gemeldet werden:

* Im iOS-SDK 4.8.6 wurde Code hinzugefügt, um besser bestimmen zu können, ob eine neue Lebenszyklussitzung tatsächlich erwünscht ist.

   Dieser Code behebt die falschen Abstürzte Nr. 2 und Nr. 3 aus dem vorherigen Abschnitt.

* Stellen Sie sicher, dass Sie Ihre Entwicklung für produktionsfremde Report Suites durchführen, was verhindern sollte, dass der falsche Absturz Nr. 1 auftritt.
* Löschen oder ändern Sie keine Werte, die das Adobe Mobile-SDK in `NSUserDefaults` setzt.

   Wenn diese Werte außerhalb des SDK modifiziert werden, sind die gemeldeten Daten ungültig.
