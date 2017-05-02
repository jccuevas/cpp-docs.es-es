---
title: "Map::GetView (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::GetView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::GetView (Método)"
ms.assetid: d432bb98-d354-4caa-8c2b-794406ac0b0b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::GetView (M&#233;todo)
Devuelve una vista de solo lectura del objeto Map actual; es decir, una [clase Platform::Collections::MapView](../cppcx/platform-collections-mapview-class.md), que implementa la interfaz [Windows::Foundation::Collections::IMapView\<K,V](http://msdn.microsoft.com/library/windows/apps/br226037.aspx).  
  
## Sintaxis  
  
```  
  
Windows::Foundation::Collections::IMapView<K, V>^   
   GetView();  
```  
  
## Valor devuelto  
 Objeto `MapView`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)   
 [Platform::Collections::UnorderedMapClass](../cppcx/platform-collections-unorderedmap-class.md)   
 [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)