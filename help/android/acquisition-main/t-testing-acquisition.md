---
description: Die folgenden Informationen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für einen Legacy-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.
keywords: android; library; mobile; sdk
seo-description: Die folgenden Informationen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für einen Legacy-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.
seo-title: Testen der Legacy-Akquise
solution: Marketing Cloud, Analytics
title: Testen der Legacy-Akquise
topic: Entwickler und Implementierung
uuid: bb 7 ace 96-68 eb -4 f 43-b 3 cf-af 80730 b 9 cee
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Testing legacy acquisition {#testing-legacy-acquisition}

Die folgenden Informationen helfen Ihnen dabei, eine Hin&amp;Zurück-Abfrage für einen Legacy-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.

Wenn die mobile App noch nicht in Google Play vorhanden ist, können Sie beim Erstellen des Kampagnenlinks eine beliebige mobile App als Ziel auswählen. Dies wirkt sich nur auf die App aus, an die Sie vom Akquise-Server umgeleitet werden, wenn Sie auf den Akquise-Link klicken und nicht auf die Möglichkeit, den Akquise-Link zu testen. Abfragezeichenfolgen-Parameter, die im Rahmen eines Kampagnen-Broadcasts an die App übergeben werden, wenn diese installiert wird, werden an den Google Play Store übergeben. Hin&amp;Zurück-Akquisetests für mobile Apps erfordern die Simulation eines solchen Broadcasts.

The app must be freshly installed, or have data cleared in **[!UICONTROL Settings]**, each time a test is run. So wird gewährleistet, dass die anfänglichen Lebenszyklusmetriken mit den Abfragezeichenfolgen-Parametern der Kampagne gesendet werden, wenn die App zum ersten Mal gestartet wird.

1. Generieren Sie in der Mobile Services UI eine URL für eine bestehende Akquise-Kampagne.

   For more information, see [Use legacy Acquisition links](/help/using/acquisition-main/c-marketing-links-builder/t-create-edit-adobe-links/c-use-legacy-acquisition-links/c-use-legacy-acquisition-links.md).
1. Verbinden Sie das Gerät mit einem Computer, starten Sie ADB Shell und rufen Sie dann die Anwendung auf dem Gerät auf.
1. Senden Sie einen Broadcast im folgenden Format:

   ```
   am broadcast -a com.android.vending.INSTALL_REFERRER -n com.example.adobetesttapp/com.google.analytics.tracking.android.CampaignTrackingReceiver --es "referrer" "utm_source=testSource&utm_medium=testMedium&utm_term=testTerm&utm_content=testContent&utm_campaign=testCampaign&trackingcode=trackingvalue"
   ```

1. Führen Sie die folgenden Schritte aus:
   1. Ersetzen Sie `com.example.adobetesttapp.com` durch den Reverse-DNS-Eintrag Ihrer Anwendung.
   1. Aktualisieren Sie die Empfängerreferenz mit der Empfängerreferenz für den Standort des Kampagnen-Trackings in Ihrer App.
   1. Replace values that are associated with `utm_source`, `utm_medium`, `utm_term`, `utm_content`, `utm_campaign`, and so on, with appropriate values.

Wenn der Broadcast erfolgreich ist, wird eine Antwort ähnlich der folgenden angezeigt:

```
Broadcasting: Intent { act=com.android.vending.INSTALL_REFERRER cmp=com.example.analyticsecommtest/com.google.analytics.tracking.android.AnalyticsReceiver has extras) } Broadcast completed: result=0
```

Darüber hinaus wird eine Bildanfrage an die Datenerfassungs-Server von Adobe gesendet. Wenn das SDK die gesamte Dauer des in Schritt 1 festgelegten Referrer-Timeouts mit einer Bildanfrage abwartet, die keine Kampagnenparameter enthält, schlägt der Broadcast fehl.