---
title: "Map::HasKey (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::HasKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::HasKey (Método)"
ms.assetid: ba7864af-056a-4b7b-843d-08c45b7f7394
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::HasKey (M&#233;todo)
Determina si el objeto Map actual contiene la clave especificada.  
  
## Sintaxis  
  
```  
  
bool HasKey(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 La clave que se usa para ubicar el elemento Map. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)