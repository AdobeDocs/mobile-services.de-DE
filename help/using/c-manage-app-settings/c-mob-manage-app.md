---
description: Sie können die Daten, die Sie von der App erhalten, verfolgen und verwalten, indem Sie verschiedene Variablen und Metriken konfigurieren.
keywords: mobile
solution: Experience Cloud Services,Analytics
title: Verwalten Ihrer App
topic-fix: Metrics
uuid: 0cc356c3-8457-40a7-8c97-7cbc68a5dc0c
exl-id: 599fef94-c188-47f5-b9d6-25a7c8cb07bc
source-git-commit: 7cfaa5f6d1318151e87698a45eb6006f7850aad4
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 93%

---

# Verwalten Ihrer App {#managing-your-app}

{#eol}

Sie können die Daten, die Sie von der App erhalten, verfolgen und verwalten, indem Sie verschiedene Variablen und Metriken konfigurieren.

## Variablen und Metriken verwalten  {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **Standardvariablen und Metriken**

   Jede App enthält Variablen und Metriken zum Tracking der Warenkorb- und Kaufaktivitäten. Einige Kaufinformationen können nicht mit Verarbeitungsregeln verarbeitet werden. Deshalb stellt das SDK die speziellen `"&&products"`-Kontextdaten bereit. Sie können beispielsweise Variablen wie „Zusatz zum Warenkorb“, „Entnahme aus Warenkorb“, „Checkouts“, „Bestellungen“ usw. verwenden. Die Kontextdaten müssen den Daten in Adobe Analytics zugeordnet werden. Wenn diese Variable mittels einer einfachen Zuordnung aus Kontextdaten aufgefüllt wird, ist dies der Schlüssel für die Zuordnung. Wenn die Variable durch komplexere Regeln in Analytics Admin Tools aufgefüllt wird, lassen Sie dieses Feld leer.

* **Benutzerdefinierte Variablen**

   Auf der Seite Benutzerdefinierte Variablen werden alle benutzerdefinierten Analytics-Variablen angezeigt, die für die Report Suite, die die Daten Ihrer App enthält, konfiguriert sind. Sie können auf dieser Seite weitere Variablen aktivieren und Kontextdaten Analytics-Variablen zuordnen.

### Kontextdaten Analytics-Variablen zuordnen

Klicken Sie auf **[!UICONTROL App-Einstellungen verwalten]** > **[!UICONTROL Variablen und Metriken verwalten]** > **[!UICONTROL Benutzerdefinierte Variablen]**.

Diese Zuordnungen rufen dieselbe API auf, die auch [Verarbeitungsregeln](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/processing-rules/processing-rules.html?lang=de) in Adobe Analytics verwenden.

![Kontextdatenzuordnung](assets/custom_data_content.png)

Im Folgenden finden Sie eine Liste der benutzerdefinierten Variablen, die Sie konfigurieren können:

* **[!UICONTROL Benutzerdefinierte Eigenschaften]** (bzw. „Props“) beantworten die Frage „Welcher/Welche/Welches?“. Props können auf einen Textwert gesetzt werden, der mit anderen Variablen und Metriken verknüpft wird, die im selben Treffer gesendet werden. Die Werte können verwendet werden, um Berichte zu filtern, oder sie können in einer Rangfolge nach einer zugehörigen Metrik aufgelistet werden.

   Wenn ein Wert für eine Eigenschaft in einem Tracking-Aufruf (oder Treffer) festgelegt wird, gilt er nur für diesen Aufruf.

* Die **[!UICONTROL Benutzerdefinierte Variablen]** (oder eVars) auch die Frage &quot;Welcher/Welche/Welches?&quot; beantworten. Ein eVar kann jedoch nicht nur auf den Treffer angewendet werden, an den er gesendet wird, sondern auch auf Variablen und Metriken, die in nachfolgenden Treffern gesendet werden, bis der Wert abläuft oder ein neuer Wert festgelegt wird.
* **[!UICONTROL Benutzerdefinierte Listenvariablen (oder mehrwertige Variablen)]** weisen das gleiche Verhalten wie Variablen auf, ermöglichen Ihnen jedoch auch, aus einem einzigen Treffer mehrere Variablen zu erfassen. Weitere Informationen finden Sie unter [Liste](https://experienceleague.adobe.com/docs/analytics/implementation/vars/page-vars/list.html?lang=de) Variablen in der Adobe Analytics-Dokumentation.

Die folgenden Zuordnungen werden in Analytics als „in Mobile Services erstellt“ angezeigt.

* **[!UICONTROL Name]**

   Der Anzeigename der Datenerfassungsvariablen.

* **[!UICONTROL Kontextdaten]**

   Wenn diese Variable mittels einer einfachen Zuordnung aus Kontextdaten aufgefüllt wird, ist dies der Schlüssel für die Zuordnung. Wenn die Variable durch komplexere Regeln in Analytics Admin Tools aufgefüllt wird, lassen Sie dieses Feld leer.

   Klicken Sie in die Kontextdatenspalte und wählen Sie die Kontextdatenvariable aus, die Sie zuordnen möchten. Die Dropdown-Liste enthält Variablen, die in den letzten 30 Tagen eingegangen sind. Wenn sich die Kontextdaten, die Sie zuordnen möchten, nicht in der Liste befinden, können Sie sie eingeben.

* **[!UICONTROL Persistenz (benutzerdefinierte Variablen und benutzerdefinierte Listenvariablen)]**

   Die Persistenz bestimmt den Punkt, an dem der Wert einer benutzerdefinierten Variable (eVar) verfällt oder an dem sie nicht mehr mit zusätzlichen Hits verknüpft wird. Wenn eine eVar bereits abgelaufen ist, wenn ein Hit auftritt, wird für diese eVar der Wert Keine mit dem Hit verknüpft. Das bedeutet, dass kein eVar-Wert aktiv war, als der Treffer ausgelöst wurde.

   Sie können eine der folgenden Optionen auswählen:

   * **[!UICONTROL Sitzung]**

      Der eVar-Wert bleibt über die Dauer des Analytics-Besuchs bestehen.

   * **[!UICONTROL Tracking-Aufruf]**

      Der eVar-Wert bleibt nur für den Tracking-Aufruf oder Treffer bestehen, in dem er enthalten war.

   * **[!UICONTROL Unbeschränkte Gültigkeit]**

      Der eVar-Wert bleibt für alle nachfolgenden Tracking-Aufrufe bestehen.
   * **[!UICONTROL Erweitert]**

      Adobe Analytics verfügt über eine erweiterte Benutzeroberfläche für die Einstellung der Persistenz von eVars. Wenn ein Persistenzwert für die eVar festgelegt wird, der in Mobile Services nicht unterstützt wird, wird dieser Wert in der Mobile Services-Benutzeroberfläche angezeigt.

      Um eVars zu verwalten, klicken Sie auf **[!UICONTROL Adobe Analytics Report Suite Manager]** > **[!UICONTROL Konversionsvariablen-Benutzeroberfläche]**.

   * **[!UICONTROL Listenunterstützung]**

      Ermöglicht die Wiedergabe mehrerer Werte, die mit der Eigenschaft verknüpft werden sollen, in einem Tracking-Aufruf. Das Trennzeichen muss ein einzelnes Zeichen sein, das weder eine Null noch ein Leerzeichen ist.

   * **[!UICONTROL Trennzeichen]**

      Das Trennzeichen muss ein einzelnes Zeichen sein, das weder eine Null noch ein Leerzeichen ist.

### Zusätzliche Analytics-Variablen

Über die Dropdownliste am Ende jedes Variablenabschnitts können Sie weitere Variablen aktivieren.

![Variable hinzufügen](assets/add_variable.png)

Wählen Sie eine nicht verwendete Variablennummer und geben Sie einen Namen ein. Sie können optional die Kontextdatenvariable, die gespeichert werden soll, sowie zusätzliche Informationen angeben.

* **Benutzerspezifische Metriken**

   Metriken (oder Ereignisse) beantworten die Fragen *wie viel?* oder *wie viele?*. Ereignisse können jedes Mal erhöht werden, wenn der Benutzer eine Aktion ausführt, oder numerische Werte wie einen Preis enthalten. Zu den benutzerdefinierten Metriken gehören Ereignisse wie das Erstellen einer App, das Herunterladen oder Exportieren der PDF- oder CSV-Datei, das Speichern einer Kampagne, das Herunterladen des SDK, das Ausführen eines Berichts, das Hinzufügen eines Links zum Appstore, das Aktivieren einer In-App-Nachricht und so weiter.

   Wählen Sie einen der folgenden benutzerdefinierten Metriktypen aus:

   * **[!UICONTROL Ganzzahl]**
   * **[!UICONTROL Dezimalzahl]**
   * **[!UICONTROL Währung]**

## Zielpunkte verwalten {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

Mithilfe von Zielpunkten können Sie geografische Standorte definieren, die Sie für Korrelationszwecke, zum Ansprechen von Zielgruppen mit In-App-Nachrichten und vieles mehr verwenden können. Wenn ein Treffer innerhalb eines Zielpunkts gesendet wird, wird der Zielpunkt an den Treffer angehängt. Weitere Informationen zu Zielpunkten finden Sie unter  [Zielpunkte verwalten](/help/using/location/t-manage-points.md).

## Link-Ziele verwalten {#section_F722A387E22A430187B063D358A87711}

Sie können Link-Ziele erstellen, bearbeiten, archivieren, dearchivieren und löschen. Diese Ziele können Sie dann inline aufrufen, wenn Sie Marketing-Links, Push-Nachrichten oder In-App-Nachrichten erstellen. Weitere Informationen zu Link-Zielen finden Sie in [Link-Ziele verwalten](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md).

## Postbacks verwalten {#section_78B0A8D7AE6940E78D85AE3AB829E860}

Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieter-Server senden. Mit denselben Triggern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Adobe Mobile so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet. Weitere Informationen zu Postbacks finden Sie unter  [Postbacks konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md).
