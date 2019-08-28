---
description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
keywords: mobile
seo-description: Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.
seo-title: Fehlerbehebung in-App-Nachrichten
solution: Marketing Cloud, Analytics
title: Fehlerbehebung in-App-Nachrichten
topic: Metriken
uuid: 39 c 3 a 21 d -92 c 2-4004-b 00 f -99 b 6 f 91 d 3696
translation-type: tm+mt
source-git-commit: 12e01e112debffd877dd62f1fd2505724b2aae7d

---


# Fehlerbehebung in-App-Nachrichten{#troubleshooting-in-app-messaging}

Diese Informationen helfen Ihnen bei der Fehlerbehebung von In-App-Nachrichten.

Wenn Sie alle Anforderungen für In-App-Nachrichten erfüllt haben, aber Nachrichten dennoch nicht angezeigt werden, überprüfen Sie Folgendes:

## Enthält die Anwendung die neue Konfiguration und das neue SDK?

Ensure that you have an [In-App Messaging](/help/android/messaging-main/messaging/messaging.md) section in your configuration (downloaded JSON file) or have a Messages remote endpoint, so that it can be retrieved from dynamic tag management.

## Meine Vollbildnachricht in Android wird nicht angezeigt. Ich verwende das richtige SDK, die richtige Konfiguration und die Auslösebedingungen sind erfüllt.

Haben Sie die Vollbildaktivität in Ihrer Manifestdatei definiert?

## Meine lokale Benachrichtigung in Android funktioniert nicht.

Stellen Sie sicher, dass der Broadcast-Empfänger für lokale Benachrichtigungen in Ihrer Manifestdatei deklariert ist. For more information, see step 2 in *Enabling In-App Messaging* in [In-App Messaging](/help/android/messaging-main/messaging/messaging.md).

## Ist die Nachricht „live“?

Um sicherzustellen, dass die Nachricht „live“ ist, überprüfen Sie auf der Seite In-App-Nachrichten verwalten in der Spalte **Status** die Liste der Nachrichten.

## Sehen Sie sich einmal ** an, *zeigen Sie einmal an*, *zeigen Sie Offline* -Einstellungen auf der Registerkarte "Zielgruppe" an.

Stellen Sie sicher, dass diese Einstellungen wie erforderlich festgelegt sind. Überprüfen Sie auf der Registerkarte **[!UICONTROL Zielgruppe]** die **Auslöser]-Optionen, mit deren Hilfe Sie festlegen können, wie oft die Nachricht angezeigt wird.[!UICONTROL **

## Wenn ein Startereignis als Auslöser verwendet wird…

Ereignis wird nur bei einer neuen Sitzung ausgelöst. Weitere Informationen dazu, wann eine Sitzung beginnt, finden Sie in der Spalte `lifecycleTimeout` unter [JSON-Konfiguration](/help/android/configuration/json-config/json-config.md).

## Ich habe meine Nachricht remote aktualisiert, in der Anwendung wird jedoch nach wie vor die alte Nachricht angezeigt.

Beachten Sie die folgenden Informationen:

* Die Aktualisierung des Endpunkts entsprechend Ihrer neuen Definition im dynamischen Tag-Management kann einige Minuten dauern. Versuchen Sie es nach einiger Zeit erneut.
* Die Konfiguration wird nur bei einem Neustart aktualisiert. Wenn die Anwendung innerhalb des Sitzungs-Timeouts des Lebenszyklus neu gestartet wurde, wurde die neue Konfiguration möglicherweise nicht heruntergeladen.

Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/android/metrics.md).

## Mein Bild passt nicht genau in den in der Vorlage vorgesehenen Platz.

Die Vollbildvorlage für In-App-Nachrichten unterstützt die Anzeige eines Bildes entweder über einen Remote-Server (Bild-URL) oder über das App-Bundle (Bundle-Bild). Das Bild sollte in einem Standard-Bildformat vorliegen, wie z. B. JPG, GIF oder PNG. Da Gerätebildschirme verschiedenste Abmessungen aufweisen, passt das Bild sehr wahrscheinlich nicht genau in den Platz der Vorlage. Die Vorlage zentriert das Bild, um die Bildmitte anzuzeigen, und schneidet Überschüssiges ab (Hochformat) bzw. lässt die Bildseiten verblassen (Querformat).

Im Folgenden finden Sie die genauen Positionierungs- und Größenregeln für jede Ausrichtung:

* **Hochformat**
   * Eine Höhe von 195 px für Smartphones.
   * Eine Höhe von 529 px für Tablets.
   * Wird zentriert, wenn das Bild breiter ist als der Bildschirm.
   * Wird abgeschnitten, wenn das Bild schmaler ist als der Bildschirm.

* **Querformat**
   * Das Bild wird auf 100 % der Bildschirmhöhe skaliert.
   * Die Breite beträgt 75 % des Bildschirms und die rechte Seite verblasst.
   Wenn Sie Probleme mit der Vollbildvorlage haben, können Sie die benutzerdefinierte HTML-Vorlage herunterladen und verwenden. Diese Vorlage bietet mehr Flexibilität in Bezug auf Bilder und gibt Ihnen volle Kontrolle über die Vorlage.
