---
title: "Map::MapChanged (Evento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::MapChanged"
ms.assetid: d14b5b93-36ff-47a5-b588-dd1dc6ea4364
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::MapChanged (Evento)
Se produce cuando un elemento se inserta en el mapa o se quita del mapa.  
  
## Sintaxis  
  
```cpp  
event Windows::Foundation::Collections::MapChangedEventHandler<K,V>^ MapChanged;  
```  
  
## Valor de propiedad y valor devuelto  
 [MapChangedEventHandler\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br206644.aspx) que contiene información sobre el objeto que desencadenó el evento y el tipo de cambio que se produjo. Consulta también [IMapChangedEventArgs\<K](http://msdn.microsoft.com/library/windows/apps/br226034.aspx) y [CollectionChange \(Enumeración\)](http://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.collectionchange.aspx).  
  
## Equivalente en .NET Framework  
 Aplicaciones de la Tienda Windows que usan interfaces IMap\<K,V\> de C\# o Visual Basic como IDictionary\<K,V\>.  
  
## Requisitos  
 Windows 8.0 o posterior  
  
## Vea también  
 [Colecciones](../cppcx/collections-c-cx.md)