---
title: "UnorderedMap::HasKey (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::HasKey"
ms.assetid: 7c397cdc-82f6-470a-8a3c-f5ba2cc58ed6
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::HasKey (M&#233;todo)
Determina si el objeto UnorderedMap actual contiene la clave especificada.  
  
## Sintaxis  
  
```scr  
  
bool HasKey(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 Clave usada para buscar el elemento UnorderedMap. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMap \(Clase\)](../cppcx/platform-collections-unorderedmap-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)   
 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)