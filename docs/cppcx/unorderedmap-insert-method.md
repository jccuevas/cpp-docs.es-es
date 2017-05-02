---
title: "UnorderedMap::Insert (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::Insert"
ms.assetid: 89d55301-3cad-4877-825b-35096a1dd740
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::Insert (M&#233;todo)
Agrega el par clave\-valor especificado al objeto UnorderedMap actual.  
  
## Sintaxis  
  
```cpp  
  
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
 `true` si la clave de un elemento del mapa actual coincide con `key` y la parte de valor de ese elemento se establece en `value`.`false` si ningún elemento existente del objeto Map actual coincide con `key` y los parámetros `key` y `value` se crean en un par clave\-valor y se agregan después al objeto UnorderedMap actual.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections