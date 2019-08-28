---
description: iOS-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK
keywords: Xamarin
seo-description: iOS-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK
seo-title: Ios-Methoden
solution: Marketing Cloud, Entwickler
title: Ios-Methoden
uuid: d 6 a 056 db -80 c 1-44 d 0-970 f-c 961 ad 01 b 0 bc
translation-type: tm+mt
source-git-commit: df4ea2c4002611c72009cf69598cbbb74b5c15c4

---


# iOS methods{#ios-methods}

iOS-Methoden für Xamarin-Komponenten für das Experience Cloud-Lösungen-4.x-SDK

## Configuration methods {#section_405AA09390E346E5BB7B1F4E0F65F51E}

* **CollectLifecycleData**

   Gibt dem SDK gegenüber an, dass Lebenszyklusdaten für die Nutzung aller Lösungen im SDK erfasst werden sollen. Weitere Informationen finden Sie unter [Lebenszyklusmetriken](/help/ios/metrics.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void CollectLifecycleData();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.CollectLifecycleData();
      ```

* **Debuglogging**

   Gibt die aktuelle Vorgabe für die Debug-Protokollierung zurück. Der Standardwert lautet `false`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static bool DebugLogging(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var debugEnabled = ADBMobile.DebugLogging();
      ```

* **SetDebugLogging**

   Aktiviert die Vorgabe für die Debug-Protokollierung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void SetDebugLogging(bool enabled); 
      
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.SetDebugLogging(true);
      
* **LifetimeValue**

   Gibt den Lebenszeitwert für den aktuellen Benutzer zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static double LifetimeValue(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var lifetimeValue = ADBMobile.LifetimeValue(); 
      ```

* **PrivacyStatus**

   Gibt die Enum-Darstellung für den Datenschutzstatus des aktuellen Benutzers zurück.
   * `ADBMobilePrivacyStatus.OptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatus.OptOut` - werden Treffer verworfen.
   * ADBMobilePrivacyStatus.Unknown: Wenn die Offline-Verfolgung aktiviert ist, werden die Zugriffe gespeichert, bis der Datenschutzstatus zu „opt-in“ (Zugriffe werden dann gesendet) oder „opt-out“ (Zugriffe werden dann verworfen) geändert wird. Wenn die Offline-Verfolgung deaktiviert ist, werden die Treffer verworfen, bis sich der Datenschutzstatus ändert.
   The default value is set in the [ADBMobileConfig.json](/help/ios/configuration/json-config/json-config.md).

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static ADBPrivacyStatus PrivacyStatus();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       var privacyStatus = ADBMobile.PrivacyStatus(); 
      ```


* **Setprivacystatus**

   Legt den Datenschutzstatus für den aktuellen Benutzer auf „status“ fest. Die folgenden Werte sind zulässig:
   * `ADBMobilePrivacyStatus.OptIn` - Treffer werden sofort gesendet.
   * `ADBMobilePrivacyStatus.OptOut` - werden Treffer verworfen.
   * `ADBMobilePrivacyStatus.Unknown`: Bei aktivierter Offline-Verfolgung werden die Treffer so lange gespeichert, bis sich der Datenschutzstatus in „opt-in“ (anschließend werden die Treffer gesendet) oder „opt-out“ (anschließend werden die Treffer verworfen) ändert. Ist die Offline-Verfolgung nicht aktiviert, werden die Zugriffe verworfen, bis der Datenschutzstatus zu „opt-in“ geändert wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void SetPrivacyStatus(ADBPrivacyStatus status) 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.SetPrivacyStatus(ADBMobilePrivacyStatus.OptIn); 
      ```

* **UserIdentifier**

   Gibt die benutzerdefinierte Benutzerkennung zurück, sofern eine benutzerdefinierte Kennung festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte Kennung festgelegt wurde. Der Standardwert lautet `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string UserIdentifier(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var userId = ADBMobile.UserIdentifier(); 
      ```

* **SetUserIdentifier**

   Gibt die benutzerdefinierte Benutzerkennung zurück, sofern eine benutzerdefinierte Kennung festgelegt wurde. Gibt null zurück, wenn keine benutzerdefinierte Kennung festgelegt wurde. Der Standardwert lautet `null`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string UserIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.SetUserIdentifier ("customUserIdentifier”); 
      ```

* **GetVersion**

   Ruft die Bibliotheksversion ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string Version();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var version = ADBMobile.Version();
      ```

* **KeepLifecycleSessionAlive (nur iOS)**

   Gibt dem SDK gegenüber an, dass beim nächsten Fortsetzen aus der Ausführung im Hintergrund keine neue Sitzung gestartet werden soll, unabhängig vom Wert für den Lebenszyklussitzungs-Timeout in der Konfigurationsdatei.

   >[!TIP]
   >
   >Diese Methode soll für Apps verwendet werden, die sich für Benachrichtigungen während des Hintergrunds registrieren und nur aus Ihrem Code aufrufen sollen, der ausgeführt wird, wenn die App im Hintergrund ausgeführt wird.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
       public static void KeepLifecycleSessionAlive();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.KeepLifecycleSessionAlive();
      ```

## Analytics methods {#section_63CF636104EF41F790C3E4190D755BBA}

* **TrackingIdentifier**

   Ruft die Analytics-Tracking-ID ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string TrackingIdentifier();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       var trackingId = ADBMobile.TrackingIdentifier();
      ```

* **TrackState**

   Verfolgt einen App-Status mit optionalen Kontextdaten. Die Statusangaben entsprechen den verfügbaren Ansichten in der App, z. B. „Titelbild“, „Level 1“ oder „Pause“. Diese Zustände ähneln Seiten einer Website und `TrackState` Aufrufe erhöhen die Seitenansichten. Wenn der Status leer ist, wird er als "App Name App Version (build)" in Berichten angezeigt. Wenn dieser Wert in einem Bericht auftritt, müssen Sie den Status in jedem `TrackState`-Aufruf festlegen.

   [!TIP]
   >Dies ist der einzige Verfolgungsaufruf, der Seitenansichten inkrementiert.
   >
   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackState(string state, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDictionary contextData; 
       contextData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val"),NSObject.FromObject("key")); 
        ADBMobile.TrackState("title screen", contextData); 
      ```

* **TrackAction**

   Verfolgt eine Aktion in der App. Aktionen sind die Vorgänge in der App, die gemessen werden sollen, z. B. „Tode“, „Level bestanden“, „Feed-Abonnements“ und weitere Metriken.

   >[!TIP]
   If you have code that might run while the app is in the background (for example, a background data retrieval), use `trackActionFromBackground` instead.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackAction(string action, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackAction("level gained", null); 
      ```

* **TrackActionFromBackground (nur iOS)**

   Verfolgt eine Aktion, die im Hintergrund abläuft. Hiermit wird das Auslösen von Lebenszyklusereignissen in bestimmten Situationen unterbunden.

   >[!TIP]
   Diese Methode sollte nur in Code aufgerufen werden, der ausgeführt wird, während sich Ihre App im Hintergrund befindet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackActionFromBackground(string action, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackActionFromBackground("majorLocationChange", null);
      ```

* **TrackLocation**

   Sendet die aktuellen Koordinaten (Längen- und Breitengrad). Ermittelt außerdem anhand der in der Datei `ADBMobileConfig.json` definierten Zielpunkte (POI), ob der als Parameter angegebene Standort in einem vorhandenen Zielpunkt liegt. Falls die aktuellen Koordinaten auf einen definierten POI passen, wird eine Kontextdatenvariable gefüllt und zusammen mit dem `TrackLocation`-Aufruf gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackLocation(CLLocation location, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      CoreLocation.CLLocation l = new CoreLocation.CLLocation  (111.111, 44.156);
      ADBMobile.TrackLocation (l, null);
      ```

* **TrackBeacon**

   Verfolgt das Eintreten eines Benutzers in den Radius eines Beacons.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackBeacon( CLBeacon beacon, NSDictionary cdata);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      CoreLocation.CLBeacon beacon = new CoreLocation.CLBeacon (); 
      ADBMobile.TrackBeacon (beacon, null);
      ```

* **TrackingClearCurrentBeacon**

   Löscht die Beacon-Daten, sobald der Benutzer den Radius des Beacons verlässt.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackingClearCurrentBeacon();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackingClearCurrentBeacon();
      ```

* **TrackLifetimeValueIncrease**

   Erhöht den Lebenszeitwert des Benutzers.

   * Hier finden Sie die Syntax für diese Methode:

      public nbsp; static void tracklifetimevalueincrease (double amount, nsdictionary cdata);

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackLifetimeValueIncrease(5, null); 
      ```

* **TrackTimedActionStart**

   Beginnt eine zeitgesteuerte Aktion mit einer benannten Aktion. Wenn Sie diese Methode für eine bereits gestartete Methode aufrufen, wird die vorherige zeitgesteuerte Aktion überschrieben.

   >[!TIP]
   Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackTimedActionStart(string action, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackTimedActionStart("level2", null);
      ```

* **TrackTimedActionUpdate**

   Übergibt Daten, mit denen die Kontextdaten für die vorliegende Aktion aktualisiert werden sollen. Die übergebenen Daten werden an die vorhandenen Daten für die Aktion angehängt. Falls ein Schlüssel bereits für die Aktion definiert ist, werden die vorhandenen Daten dieses Schlüssels überschrieben.

   >[!TIP]
   Dieser Aufruf sendet keinen Treffer.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackTimedActionUpdate(string action, NSDictionary cdata); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDictionary updatedData = NSDictionary.FromObjectAndKey (NSObject.FromObject("val2"), NSObject.FromObject ("key2")); 
        ADBMobile.TrackTimedActionUpdate("level2", updatedData); 
      ```

* **TrackTimedActionEnd**

   Beendet eine zeitgesteuerte Aktion.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackTimedActionEnd(string action, Func<double, double, NSMutableDictionary, sbyte> block); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("level2", (double  arg1,  double  arg2,  NSMutableDictionary  arg3)  =>  { 
      return  Convert.ToSByte(true); 
      }); 
      
* **TrackingTimedActionExists**

   Gibt zurück, ob eine zeitgesteuerte Aktion ausgeführt wird (oder nicht).

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static bool TrackingTimedActionExists(string action); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackTimedActionEnd  ("timedAction",  (double  inAppDuration, 
      double  totalDuration,  NSMutableDictionary  data)  =>  { 
                   return  true; 
      });
      ```

* **TrackingSendQueuedHits**

   Erzwingt in der Bibliothek das Senden aller Zugriffe aus der Offline-Warteschlange, unabhängig von der Anzahl der Zugriffe.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackingSendQueuedHits();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TrackingSendQueuedHits(); 
      ```

* **TrackingClearQueue**

   Löscht alle Zugriffe aus der Offline-Warteschlange.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TrackingClearQueue(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       ADBMobile.TrackingClearQueue();
      ```

* **TrackingGetQueueSize**

   Ruft die Anzahl der Zugriffe ab, die sich derzeit in der Offline-Warteschlange befinden.

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      public static int TrackingGetQueueSize();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var queueSize = ADBMobile.TrackingGetQueueSize(); 
      ```

## Experience Cloud ID methods {#section_157919E46030443DBB5CED60D656AD9F}

* **GetMarketingCloudID**

   Ruft die Experience Cloud ID vom ID-Service ab.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string GetMarketingCloudID(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      var mcid = ADBMobile.GetMarketingCloudID();
      ```

* **VisitorSyncIdentifiers**

   Mit der Experience Cloud ID können Sie weitere Kunden-IDs festlegen, die den einzelnen Besuchern zugewiesen werden. Die Besucher-API akzeptiert mehrere Kunden-IDs für denselben Besucher sowie eine Kundentypkennung, die den Umfang der einzelnen Kunden-IDs abgrenzt. Diese Methode entspricht setCustomerIDs in der JavaScript-Bibliothek.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void VisitorSyncIdentifiers(NSDictionary identifiers);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       NSDictionary  ids  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("pushID")); 
       ADBMobile.VisitorSyncIdentifiers(ids); 
      ```

## Target-Methoden {#section_C1E4121CAF9D43538511D857A1F549A7}

* **TargetLoadRequest**

   Sendet request an Ihren konfigurierten Target-Server und gibt den Zeichenfolgenwert des in einem -`Action<NSDictionary>`Callback generierten Angebots zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TargetLoadRequest (ADBTargetLocationRequest request, Action<NSString> callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
       ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
       ADBMobile.TargetLoadRequest(req,    (context)  =>  { 
       Console.WriteLine  (context); 
       });
      ```

* **TargetCreateRequest**

   Vordefinierter Konstruktor zum Erzeugen eines `ADBTargetLocationRequest`-Objekts mit den angegebenen Parametern.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDictionary  dict  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBTargetLocationRequest  req  =  ADBMobile.TargetCreateRequest  ("iOSTest",  "defGal",  dict); 
      ```

* **TargetCreateOrderConfirmRequest**

   Erstellt eine `ADBTargetLocationRequest`.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static ADBTargetLocationRequest ADBTargetLocationRequest TargetCreateRequest (string name, string defaultContent, NSDictionary parameters);
      
   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TargetCreateOrderConfirmRequest ("myOrder", "12345", "29.41", "cool stuff", null); 
      ```

* **TargetClearCookies**

   Löscht alle Ziel-Cookies aus der App.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void TargetClearCookies(); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.TargetClearCookies(); 
      ```

## Audience Manager {#section_862C4202B6294B978DEEBB15C5CD5C01}

* **AudienceVisitorProfile**

   Gibt das zuletzt erfasste Besucherprofil zurück. Gibt null zurück, falls noch kein Signal übertragen wurde. Das Besucherprofil wird in `NSUserDefaults` gespeichert und steht so bei jedem Start der Anwendung zur Verfügung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static NSDictionary AudienceVisitorProfile (); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDictionary profile = ADBMobile.AudienceVisitorProfile();
      ```

* **AudienceDpid**

   Gibt die aktuelle DPID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string AudienceDpid ();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      string currentDpid = ADBMobile.AudienceDpid();
      ```

* **AudienceDpuuid**

   Gibt die aktuelle DPUUID zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static string AudienceDpuuid ();
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      string currentDpuuid = ADBMobile.AudienceDpuuid(); 
      ```

* **AudienceSetDpidAndDpuuid**

   Legt die DPID und die DPUUID fest. Wenn die DPID und die DPUUID festgelegt sind, werden sie mit jedem Signal gesendet.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void AudienceSetDpidAndDpuuid (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.AudienceSetDpidAndDpuuid ("testDppid", "testDpuuid")
      ```

* **AudienceSignalWithData**

   Sends audience management a signal with traits and get the matching segments returned in a `Action<NSDictionary>`  callback.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void AudienceSignalWithData (NSDictionary data, Action<NSDictionary> callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      NSDictionary  audienceData  =  NSDictionary.FromObjectAndKey  (NSObject.FromObject  ("value2"),  NSObject.FromObject  ("key1")); 
      ADBMobile.AudienceSignalWithData  (audienceData,  (context)  =>  { 
      Console.WriteLine  (context); 
      }); 
      ```

* **AudienceReset**

   Setzt die UUID des Zielgruppen-Managers zurück und löscht das aktuelle Besucherprofil.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void AudienceReset ();
      ```

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      ADBMobile.AudienceReset ();
      ```

## Video {#section_CBCE1951CE204A108AD4CA7BB07C7F98}

Weitere Informationen finden Sie unter [Videoanalysen](/help/ios/getting-started/dev-qs.md).

* **MediaCreateSettings**

   Gibt ein `ADBMediaSettings`-Objekt mit den angegebenen Parametern zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static ADBMediaSettings MediaCreateSettings ([string name, double length, string playerName, string playerID); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings ("name1", 10, "playerName1", "playerID1"); 
      ```

* **MediaAdCreateSettings**

   Gibt ein `ADBMediaSettings`-Objekt für die Verfolgung einer Videoanzeige zurück.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static ADBMediaSettings MediaAdCreateSettings ( string name,  double length,  string playerName,  string parentName,  string parentPod,  double parentPodPosition,  string CPM); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMediaSettings adSettings = ADBMobile.MediaAdCreateSettings("adName1", 2, "playerName1", "name1", "podName1", 4, "CPM1");
      ```

* **MediaOpenWithSettings**

   Öffnet ein `ADBMediaSettings`-Objekt für die Verfolgung.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaOpenWithSettings ( ADBMediaSettings settings,  Action<ADBMediaState> callback); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMediaSettings settings = ADBMobile.MediaCreateSettings  ("name1",  10,  "playerName1",  "playerID1"); 
      ADBMobile.MediaOpenWithSettings  (settings,  (state)  =>  { 
      Console.WriteLine  (state.Name); 
      }); 
      ```

* **MediaClose**

   Schließt das angegebene Medienelement.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaClose ( string name);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.MediaClose  (settings.Name);
      ```

* **MediaPlay**

   Gibt das angegebene Medienelement am angegebenen Offset (in Sekunden) wieder.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaPlay ( string name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.MediaPlay (settings.Name, 0); 
      ```

* **MediaComplete**

   Kennzeichnet das Medienelement am angegebenen Offset (in Sekunden) als abgeschlossen.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaComplete ( string name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
      ADBMobile.MediaComplete (settings.Name, 5);
      ```

* **MediaStop**

   Benachrichtigt das Medienmodul, dass das Video am angegebenen Offset beendet oder angehalten wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaStop ( string name, double offset);
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       ADBMobile.MediaStop (settings.Name, 3);
      ```

* **MediaClick**

   Benachrichtigt das Medienmodul darüber, dass das Medienelement angeklickt wurde.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaClick ( string name, double offset); 
      ```

* **MediaTrack**

   Sendet einen Verfolgungsaktionsaufruf (keine Seitenansicht) für den aktuellen Medienstatus.

   * Hier finden Sie die Syntax für diese Methode:

      ```objective-c
      public static void MediaTrack ( string name, NSDictionary data); 
      ```

   * Hier finden Sie ein Code-Beispiel für diese Methode:

      ```objective-c
       ADBMobile.MediaTrack (settings.Name, null);
      ```