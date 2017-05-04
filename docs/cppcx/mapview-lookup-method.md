---
title: "MapView::Lookup (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::Lookup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::Lookup (Método)"
ms.assetid: 93090ac3-3f1d-4b7e-b80e-164b8c65cd29
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::Lookup (M&#233;todo)
Recupera el valor de tipo V asociado a la clave especificada de tipo K.  
  
## Sintaxis  
  
```  
V Lookup(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 La clave utilizada para buscar un elemento en el objeto MapView. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 El valor que se empareja con `key`. El tipo del valor devuelto es typename *V*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md)