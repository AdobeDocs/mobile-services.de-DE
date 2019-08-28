---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax innerhalb des Kontextdatenparameters verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Marketing Cloud, Analytics
title: Ereignis-Serialisierung
topic: Entwickler und Implementierung
uuid: 7220 a 001-1174-4013-91 ff-e 8603 d 8 ab 265
translation-type: tm+mt
source-git-commit: f5ba33fe805c502b8ae91ddafcaa0b57e68704b8

---


# Ereignis-Serialisierung {#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im mobilen SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt im Serveraufruf festzulegen.

```js
cdata["&&events"] = "event1:12341234";
```

Beispiel:

```js
//create a context data dictionary 
var cdata = new Windows.Foundation.Collections.PropertySet(); 
 
// add events 
cdata["&&events"] = "event1:12341234"; 
 
var ADB = ADBMobile; 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
ADB.Analytics.trackAction("action", cdata); 
// trackState example: 
ADB.Analytics.trackState("State Name", cdata);
```
