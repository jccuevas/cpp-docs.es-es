---
title: "Map::Lookup (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Lookup (Método)"
ms.assetid: c56773ae-2df0-4d21-a6ab-9603529547b0
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Lookup (M&#233;todo)
Recupera el valor de tipo V asociado a la clave especificada de tipo K, si la clave existe.  
  
## Sintaxis  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 La clave utilizada para buscar un elemento en el objeto Map. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  
## Comentarios  
 Si no existe la clave, se produce una excepción [Platform::OutOfBoundsException](../cppcx/platform-outofboundsexception-class.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)   
 [Colecciones \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)