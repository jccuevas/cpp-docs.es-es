---
title: "UnorderedMapView::Lookup (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::Lookup"
ms.assetid: 22f61824-ba8c-4b8c-9077-7577c41a6742
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::Lookup (M&#233;todo)
Recupera el valor de tipo V asociado a la clave especificada de tipo K.  
  
## Sintaxis  
  
```cpp  
V Lookup(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 Clave usada para buscar un elemento en UnorderedMapView. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMapView \(Clase\)](../cppcx/platform-collections-unorderedmapview-class.md)