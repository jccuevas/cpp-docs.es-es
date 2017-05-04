---
title: "UnorderedMap::MapChanged | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::MapChanged"
ms.assetid: 6863781e-35af-4e77-9a11-277bd00f5d41
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::MapChanged
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