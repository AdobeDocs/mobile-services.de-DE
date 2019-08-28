---
description: Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können.
seo-description: Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können.
seo-title: Apple-Suchanzeigen
solution: Marketing Cloud, Analytics
title: Apple-Suchanzeigen
topic: Entwickler und Implementierung
uuid: 790080 e 8-067 e -4 bfd-a 169-0027 db 4 fdff 3
translation-type: tm+mt
source-git-commit: 9c6923d14d1a5f30e5873299def61b0734e52429

---


# Apple-Suchanzeigen {#apple-search-ads}

Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können. Weitere Informationen zu Suchanzeigekampagnen finden Sie unter [Apple-Suchanzeigen](https://searchads.apple.com).

## Vorteile {#section_CEA30C652AC8470784B8054E299B80FA}

Vorteile durch die Verwendung von Apple-Werbeanzeigen:

* Einfaches Messen der Effektivität Ihrer Suchanzeigen-App-Downloadkampagnen durch das Hinzufügen von ein paar Codezeilen zu Ihrer App.
* Entwickler können auf das Datum bzw. die Uhrzeit des Downloads sowie auf das gebotene Keyword zugreifen, das die Konversion verursacht hat.

## Implementieren von Apple-Werbeanzeigen {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Zur Implementierung von Apple Ads benötigen Sie ios SDK 4.13.2 oder höher.

So aktivieren Sie Ihre App für die Suchanzeigenzuordnung:

1. Implementieren Sie das Adobe-SDK, Version 4.13.2 oder höher.

   Weitere Informationen finden Sie unter [Core-Implementierung und -lebenszyklus](/help/ios/getting-started/dev-qs.md).

1. Fügen Sie das iAd-Framework zu Ihrer Xcode-Projektdatei für Ihre App hinzu.

## Erstellen von Berichten zur Suchanzeigenzuordnung {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple-Suchanzeigen-Zuordnungsdaten werden im Akquisenamen, in der Quelle und den Begriffswerten angegeben.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   Zusätzlich werden die folgenden Werte aus dem „`iad`“-Wörterbuch zu unseren typischen Akquisitionskontext-Datenfeldern zugeordnet:

   * " `iad-campaign-id`" --&gt; " `a.referrer.campaign.trackingcode`"
   * " `iad-campaign-name`" --&gt;" `a.referrer.campaign.name``"
   * " `iad-adgroup-id`" --&gt; " `a.referrer.campaign.content`"
   * " `iad-keyword`" --&gt; " `a.referrer.campaign.term`"
   Durch diese Zuordnung werden die Werte in unserer Standardberichterstellung zur Verfügung gestellt.
