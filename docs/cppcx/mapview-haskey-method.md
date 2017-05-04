---
title: "MapView::HasKey (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::HasKey"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::HasKey (Método)"
ms.assetid: c1a24f63-e6fd-4cfd-90ce-b89352b98324
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::HasKey (M&#233;todo)
Determina si el objeto MapView actual contiene la clave especificada.  
  
## Sintaxis  
  
```  
  
bool HasKey(  
   K key  
);  
```  
  
#### Parámetros  
 `key`  
 La clave que se usa para ubicar el elemento MapView. El tipo de `key` es typename *K*.  
  
## Valor devuelto  
 `true` si se encuentra la clave; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md)