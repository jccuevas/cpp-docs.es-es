---
title: "UnorderedMapView::HasKey (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::HasKey"
ms.assetid: 4704da18-8606-4df7-be51-d125b2e4aee0
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::HasKey (M&#233;todo)
Determina si el objeto UnorderedMap actual contiene la clave especificada.  
  
## Sintaxis  
  
```cpp  
  
bool HasKey(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 La clave utilizada para buscar el elemento. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMap \(Clase\)](../cppcx/platform-collections-unorderedmap-class.md)   
 [Colecciones](../cppcx/collections-c-cx.md)   
 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)