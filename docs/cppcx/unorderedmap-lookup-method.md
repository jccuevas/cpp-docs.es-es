---
title: "UnorderedMap::Lookup (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::Lookup"
ms.assetid: 6f9bb393-3791-423d-bfee-925e0531e1a5
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::Lookup (M&#233;todo)
Recupera el valor de tipo V asociado a la clave especificada de tipo K.  
  
## Sintaxis  
  
```scr  
V Lookup(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 Clave usada para buscar un elemento en el objeto UnorderedMap. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Colecciones](../cppcx/collections-c-cx.md)   
 [Platform::Collections::UnorderedMap \(Clase\)](../cppcx/platform-collections-unorderedmap-class.md)