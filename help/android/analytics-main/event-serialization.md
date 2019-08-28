---
description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
keywords: android; library; mobile; sdk
seo-description: Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.
seo-title: Ereignis-Serialisierung
solution: Marketing Cloud, Analytics
title: Ereignis-Serialisierung
topic: Entwickler und Implementierung
uuid: acdeda 16-ab 83-4 cfc -907 d -33448 b 801 b 31
translation-type: tm+mt
source-git-commit: bf076aa8e59d5c3e634fc4ae21f0de0d4541a83f

---


# Ereignis-Serialisierung {#event-serialization}

Die Ereignis-Serialisierung wird von Verarbeitungsregeln nicht unterstützt. Im Mobile-SDK müssen Sie eine spezielle Syntax im Kontextdatenparameter verwenden, um serialisierte Ereignisse direkt beim Server-Aufruf festzulegen.

```java
cdata.put("&&events", "event1:12341234");
```

Beispiel:

```java
//create a context data dictionary 
HashMap cdata = new HashMap<String, Object>(); 
 
// add events 
cdata.put("&&events", "event1:12341234"); 
 
// send the tracking call - use either a trackAction or TrackState call. 
// trackAction example: 
Analytics.trackAction("action", cdata); 
// trackState example: 
Analytics.trackState("State Name", cdata);
```
