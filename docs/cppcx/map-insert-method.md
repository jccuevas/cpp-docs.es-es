---
title: "Map::Insert (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Insert"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Insert"
ms.assetid: 3acb2221-c12f-407a-a570-2e52df3569f6
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Insert (M&#233;todo)
Agrega el par clave\-valor especificado al objeto Map actual.  
  
## Sintaxis  
  
```  
  
virtual bool Insert(  
   K key,   
   V value  
);  
```  
  
#### Parámetros  
 `key`  
 La parte de clave del par clave\-valor. El tipo de `key` es typename *K*.  
  
 `value`  
 La parte de valor del par clave\-valor. El tipo de `value` es typename *V*.  
  
## Valor devuelto  
 `true` si la clave de un elemento del mapa actual coincide con `key` y la parte de valor de ese elemento se establece en `value`.`false` si ningún elemento existente del mapa actual coincide con `key` y los parámetros `key` y `value` se crean en un par clave\-valor y se agregan después al mapa actual.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)