---
description: Im Folgenden finden Sie einige Informationen zur Messung von Videos unter Android mithilfe der Videomessung.
keywords: android; library; mobile; sdk
seo-description: Im Folgenden finden Sie einige Informationen zur Messung von Videos unter Android mithilfe der Videomessung.
seo-title: Video-Analytics
solution: Marketing Cloud, Analytics
title: Video-Analytics
topic: Entwickler und Implementierung
uuid: a 137 cc 27-dc 28-48 c 0-b 08 e -2 ca 17 d 2 c 7 e 1 d
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Video Analytics  {#video-analytics}

Im Folgenden finden Sie einige Informationen zur Messung von Videos unter Android mithilfe der Videomessung.

>[!TIP]
>
>Während der Videowiedergabe werden diesem Dienst häufige Heartbeat-Aufrufe gesendet, um die wiedergegebene Zeit zu messen. Diese Heartbeat-Aufrufe werden alle 10 Sekunden gesendet. Dies führt zu detaillierten Videointeraktionsmetriken und genaueren Video-Fallout-Berichten. Weitere Informationen zur Videomessungslösung von Adobe finden Sie unter [Messen von Audio und Video in Adobe Analytics](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html).

Der allgemeine Prozess zur Videomessung ist für alle Plattformen ähnlich. Hier finden Sie eine Übersicht der Entwickleraufgaben samt Code-Beispielen. In der folgenden Tabelle finden Sie die Mediendaten, die an Analytics gesendet werden. Verarbeitungsregeln werden verwendet, um die Kontextdaten einer Analytics-Variablen zuzuordnen.

## Map player events to Analytics variables {#section_E84987F878AB4A3A83AE700FEC4C9D4D}

* **a.media.name**
   * Variablentyp: Evar
      * Standardgültigkeit: Besuch
      * Benutzerspezifischer Insight-Bericht (s.prop, wird zur Videopfadsetzung verwendet)
   * (**Erforderlich**) Wenn ein Besucher das Video auf irgendeine Weise betrachtet, erfasst diese Kontextdatenvariable den Namen des Videos, wie in der Implementierung angegeben. Sie können Classifications für diese Variable hinzufügen.
   * (**Optional**) Die Variable „Benutzerspezifischer Insight-Bericht “ bietet Informationen für die Videopfadgebung.

* **a.media.name**
   * Variablentyp: Custom Insight (s. prop)
   * (**Optional**) Bietet Informationen zur Videopfadsetzung.

      >[!IMPORTANT]
      >
      >Die Pfade müssen für diese Variable von expcare aktiviert werden.
   * Ereignistyp: Benutzerspezifischer Insight-Bericht (s.prop)

* **a.media.segment**
   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht
   * (**Erforderlich**) Erfasst Videosegmentdaten, einschließlich Segmentname und Reihenfolge, in der das Segment im Video erscheint.

      Diese Variable wird gefüllt, indem Sie beim automatischen Verfolgen von Player-Ereignissen die Variable `segmentByMilestones` aktivieren oder beim manuellen Verfolgen der Player-Ereignisse einen benutzerdefinierten Segmentnamen festlegen. Beispiel: Wenn ein Besucher das erste Segment in einem Video ansieht, kann SiteCatalyst Folgendes in der Segment-eVar erfassen: `1:M:0-25`.

      Die standardmäßige Methode zur Videodatenerfassung sammelt Daten an folgenden Punkten:

      * Videostart (Wiedergabe)
      * Segmentbeginn
      * Videoende (Stopp)
      Analytics zeichnet die erste Segmentansicht am Anfang des Segments auf, wenn der Besucher die Wiedergabe startet. Nachfolgende Segmentansichten werden aufgezeichnet, wenn das jeweilige Segment anfängt.


* **a.contentType**
   * Variablentyp: Evar
   * Standardgültigkeit: Seitenansicht
   * Erfasst Daten zum Typ des Inhalts, der von einem Besucher angesehen wird.

      Den von der Videomessung gesendeten Treffern wird der Content-Typ `video` zugewiesen. Im Hinblick auf die Videomessung können Sie über den **Content-Typ** Videobesucher identifizieren und somit Videokonversionsraten berechnen.

* **a.media.timePlayed**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt in Sekunden an, wie lange ein Video seit dem letzten Datenerfassungsprozess (Bildanfrage) wiedergegeben wurde.

* **a.media.view**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher einen Teil eines Videos betrachtet hat.

      Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

* **a.media.segmentView**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher einen Teil eines Videosegments betrachtet hat.

      Es werden jedoch keine Informationen zu der Länge oder dem Ausschnitt des vom Besucher angesehenen Videos bereitgestellt.

* **a .media.complete**
   * Variablentyp: Ereignis
   * Typ: Zähler
   * Gibt an, dass ein Besucher ein Video vollständig angesehen hat.

      Standardmäßig wird das complete-Ereignis 1 Sekunde vor dem Ende des Videos gemessen. Bei der Implementierung können Sie festlegen, ab wie vielen Sekunden vor Ende des Videos die Ansicht als vollständig betrachtet werden soll. Bei Live-Videoinhalten und anderen Streams, die nicht über ein definiertes Ende verfügen, können Sie einen benutzerdefinierten Zeitpunkt festlegen, um abgeschlossene Ansichten zu messen (z. B. nach einer bestimmten Wiedergabedauer).


## Configure media settings {#section_929945D4183C428AAF3B983EFD3E2500}

Konfigurieren Sie ein `MediaSettings`-Objekt mit den Einstellungen, die Sie zur Videoverfolgung verwenden möchten:

```java
MediaSettings mySettings = Media.settingsWith("name", 10, "playerName", "playerId");
```

## Track player events {#section_C7F43AECBC0D425390F7FCDF3035B65D}

To measure video playback, the `mediaPlay`, `mediaStop`, and `mediaClose` methods need to be called at the appropriate times. Wenn beispielsweise der Player angehalten wird, muss `mediaStop` aufgerufen werden. `mediaPlay` wird aufgerufen, wenn die Wiedergabe gestartet oder fortgesetzt wird.

## Klassen {#section_16838332727348F990305C0C6B0D795C}

**Klasse: MediaSettings**

```java
public String name; 
public String playerName; 
public String playerID; 
public double length; 
public String channel; 
public String milestones; 
public String offsetMilestones; 
public boolean segmentByMilestones; 
public boolean segmentByOffsetMilestones; 
public int trackSeconds = 0; 
public int completeCloseOffsetThreshold = 1; 
 
// MediaAnalytics Ad settings 
public String parentName; 
public String parentPod; 
public String CPM; 
public double parentPodPosition; 
public boolean isMediaAd;
```

**Klasse: MediaState**

```java
public Date openTime = new Date(); 
public String name; 
public String segment; 
public String playerName; 
public String mediaEvent; 
public int offsetMilestone; 
public int segmentNum; 
public int milestone; 
public double length; 
public double offset; 
public double percent; 
public double timePlayed; 
public double segmentLength; 
public boolean complete = false; 
public boolean clicked = false; 
public boolean ad; 
public boolean eventFirstTime;
```

## Media Measurement class and method reference {#section_50DF9359A7B14DF092634C8E913C77FE}

Die folgenden Methoden sind in der Media Measurement-Klasse verfügbar:

* **settingsWith**

   Gibt ein `MediaSettings`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      MediaSettingsmySettings = Media.settingsWith("name", 10, "playerName", "playerId");
      ```

* **adSettingsWith**

   Gibt ein `MediaSettings`-Objekt zur Verfolgung einer Videoanzeige zurück.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static MediaSettings adSettingsWith(String name, double length, String playerName, String parentName, String parentPod, double parentPodPosition, String CPM);
      ```

* **open**

   Öffnet ein `MediaSettings`-Objekt zur Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void open(MediaSettings settings, MediaCallback callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.open(mySettings, new Media.MediaCallback() { 
        @Override 
        public void call(Object item)
        {//  monitor  callback  if  you  want  to  be  notified  every  second  the  media  is  playing  }
        }); 
      ```

   * **close**

      Schließt das Medienelement mit dem Namen *name*.

      * Hier finden Sie die Syntax für diese Methode:
      ```java
      public static void close(String name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.close("name"); 
      ```


* **play**
   * Gibt das Medienelement namens *Name* mit dem Versatz *offset* (in Sekunden) wieder.
   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstatic void play(String name, double offset); 
      ```

* **Fertig**

   Kennzeichnet das Medienelement mit dem Versatz *Offset* (in Sekunden) manuell als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void complete(String name, double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.complete("name", 0); 
      ```

* **stop**

   Benachrichtigt das Medienmodul darüber, dass das Video mit dem Versatz *Offset* beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void stop(String name, double offset); 
      ```

   * Im Folgenden finden Sie das Codebeispiel oder die folgende Methode:

      ```java
      Media.stop("name", 0);
      ```

* **click**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      public static void click(String name double offset); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.click("name", 0);
      ```

* **track**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```java
      publicstatic void track(String name, Map<String, Object> data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```java
      Media.track("name", null); 
      ```