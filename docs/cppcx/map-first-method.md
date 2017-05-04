---
title: "Map::First (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::First (Método)"
ms.assetid: bb1a4458-ecc3-43b0-b808-1693f853ad82
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::First (M&#233;todo)
Devuelve un iterador que especifica el primer elemento del mapa o `nullptr` si el mapa está vacío.  
  
## Sintaxis  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
## Valor devuelto  
 Un iterador que especifica el primer elemento del mapa.  
  
## Comentarios  
 Una manera cómoda de contener el iterador devuelto por First \(\) es asignar el valor devuelto a una variable que se declare con la palabra clave de deducción de tipos [automática](~/cpp/auto-cpp.md). Por ejemplo: `auto x = myMap->First();`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)   
 [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)