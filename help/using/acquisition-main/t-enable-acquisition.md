---
description: Das Akquise-Tracking muss in der SDK-Konfiguration aktiviert sein, damit Marketing-Links verfolgt und in Berichten verwendet werden können.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Akquise konfigurieren
topic-fix: Metrics
uuid: e996e43e-8a77-47a3-a6fb-53f676f92bef
exl-id: 3a12dfab-70d0-41e6-8d4e-5aba21bb8606
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---

# Akquise konfigurieren {#configure-acquisition}

{#eol}

Das Akquise-Tracking muss in der SDK-Konfiguration aktiviert sein, damit Marketing-Links verfolgt und in Berichten verwendet werden können.

1. Rufen Sie die Seite „App-Einstellungen verwalten“ für die gewünschte App auf und scrollen Sie zum Abschnitt **[!UICONTROL SDK-Akquise-Optionen]** herunter.
1. Führen Sie die folgenden Aufgaben aus:

   * Um die Akquise zu aktivieren, aktivieren Sie das Kontrollkästchen **[!UICONTROL Aktivieren]**.

      Wenn Sie dieses Kontrollkästchen aktivieren, wird das Feld **[!UICONTROL Referrer-Timeout]** angezeigt und der Wert wird von 0 in 5 geändert.

   * Geben Sie im Feld **[!UICONTROL Referrer-Timeout (Sekunden)]** einen Wert ein.

      (**Optional**) Wenn Sie das Kontrollkästchen **[!UICONTROL Aktivieren]** aktiviert haben, ist dieses Feld optional. Sie können den Timeout-Wert ändern, indem Sie einen Sekundenwert eingeben. Diese Einstellung legt die Zeit fest, die auf Akquise-Informationen gewartet werden soll, bevor ein „Erster Start“-Treffer gesendet wird.
   >[!IMPORTANT]
   >Sie müssen einen Wert ungleich Null eingeben. Wenn Sie die Akquise aktivieren, aber der Wert Null ist, funktionieren die Akquise-Links nicht. Es wird empfohlen, den Standardwert von 5 Sekunden zu verwenden.

1. Laden Sie die neue SDK-Konfigurationsdatei herunter und verwenden Sie sie in Ihrer App.

   Sie haben die Akquise für **iOS** erfolgreich konfiguriert. 

