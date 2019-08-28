---
description: Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.
keywords: mobile
seo-description: Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.
seo-title: Fehlerbehebung von In-App-Nachrichten
solution: Marketing Cloud, Analytics
title: Fehlerbehebung von In-App-Nachrichten
topic: Metriken
uuid: 8813 e 8 d 8-bb 1 e -46 ad -83 cd -98 ae 68 f 73 ce 6
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting in-app messaging{#troubleshooting-in-app-messaging}

Diese Informationen unterstützen Sie bei der Lösung von Problemen mit In-App-Nachrichten.

Wenn alle Anforderungen für In-App-Nachrichten erfüllt sind, die Nachrichten jedoch nicht angezeigt werden, überprüfen Sie die folgenden Punkte:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

* Stellen Sie sicher, dass Sie die SDK-Version 4.2 (oder höher) verwenden und dass sie ordnungsgemäß konfiguriert ist.

* Ensure that you have a [Messaging](/help/using/in-app-messaging/in-app-messaging.md) section in your configuration (the downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Meine Vollbildnachricht in Android wird nicht angezeigt. Ich verwende das richtige SDK, die richtige Konfiguration und die Auslösebedingungen sind erfüllt.

Haben Sie die Vollbildaktivität in Ihrer Manifestdatei definiert?

## Meine lokale Benachrichtigung in Android funktioniert nicht.

Stellen Sie sicher, dass der lokale Empfänger für übertragene Benachrichtigungen in Ihrer Manifestdatei deklariert ist. For more information, see step #1 in [In-app messaging](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Anhand der Listenansicht in der Spalte **[!UICONTROL Status]** auf der Seite In-App-Nachricht verwalten können Sie überprüfen, ob die Nachricht live ist.

## Sehen Sie sich einmal ** an, *zeigen Sie einmal an*, *zeigen Sie Offline* -Einstellungen auf der Seite Zielgruppe an.

Stellen Sie sicher, dass die Einstellungen korrekt sind. Überprüfen Sie auf der Seite Zielgruppe die Optionen auf der Registerkarte **Auslöser**. Hier können Sie angeben, wie oft die Nachricht angezeigt wird.

## Bei Verwendung eines Ereignisstarts als Auslöser...

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Informationen dazu, wann eine Sitzung beginnt, finden Sie unter `lifecycleTimeout` in der [adbmobile](/help/ios/configuration/json-config/json-config.md) JSON-Konfigurationsdatei.

## Ich habe meine Nachricht remote aktualisiert; in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Führen Sie eine der folgenden Aufgaben aus:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern.

   Warten Sie einige Minuten und versuchen Sie es ggf. erneut.

* Die Konfiguration wird nur bei einem Neustart aktualisiert.

   Wenn die App innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

## Mein Bild passt nicht genau in den in der Vorlage vorgesehenen Platz.

Die Vollbildvorlage für In-App-Nachrichten unterstützt die Anzeige eines Bildes über einen Remote-Server (Bild-URL) oder über das App-Bundle (Bild-Bundle). Das Bild sollte in einem Standardbildformat vorliegen, wie z. B. JPG, GIF oder PNG.

Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild wahrscheinlich nicht genau in den Platz, der in der Vorlage vorgesehen ist. Die Vorlage versucht stets, die Mitte des Bildes zu zeigen, und schneidet die Seiten zu (Hochformat) bzw. blendet sie aus (Querformat), wenn das Bild nicht passt.

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat:** Das Bild wird auf eine Höhe von 195 px für Smartphones bzw. 529 px für Tablets skaliert und zentriert, wenn die Bildbreite kleiner als die Breite des Geräts ist, bzw. zugeschnitten, wenn die Bildbreite größer als die Breite des Geräts ist.

* **Querformat:** Das Bild wird auf 100 % der Höhe und 75 % der Gerätebreite skaliert, wobei es nach rechts hin ausgeblendet wird.

   Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Die benutzerdefinierte HTML-Vorlage bietet mehr Flexibilität in Bezug auf Bilder und gibt Ihnen volle Kontrolle über die Vorlage.

## In meinen Nachrichten erscheinen keine Änderungen/Aktualisierungen, die ich über die Benutzeroberfläche vorgenommen habe.

Das SDK ruft neue/aktualisierte Nachrichten zum Zeitpunkt eines Lebenszyklusstarts ab. Dies passiert erst, wenn die Anwendung für einen Zeitraum, der den Timeout-Wert für den Lebenszyklus überschreitet, geschlossen/in den Hintergrund verschoben und dann erneut geöffnet wird.

Führen Sie die folgenden Schritte aus:

1. Zeigen Sie die Nachrichten-URL in Ihrer Konfigurationsdatei an, um zu überprüfen, ob die Remote-Nachricht aktualisiert wird (z. `curl "https://assets.adobedtm.com/b213090c5204bf94318f4ef0539a38b487d10368/scripts/satellite-542c62859662383b1a0008f4.json"`B.).
1. Schließen Sie die Anwendung.
1. Wait for a time period that is longer than the `lifecycleTimeout` in the config file.
1. Öffnen Sie die App, navigieren Sie zu der Stelle, an der die Nachricht angezeigt werden soll, und überprüfen Sie, ob sie aktualisiert wurde.