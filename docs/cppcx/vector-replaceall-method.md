---
title: "Vector::ReplaceAll (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::ReplaceAll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::ReplaceAll"
ms.assetid: dec905f9-80fc-4aa0-ad04-bbab10feb0b2
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::ReplaceAll (M&#233;todo)
Elimina los elementos del objeto Vector actual y después inserta los elementos de la matriz especificada.  
  
## Sintaxis  
  
```  
  
virtual void ReplaceAll(  
   const ::Platform::Array<T>^ arr  
);  
```  
  
#### Parámetros  
 `arr`  
 Una matriz de objetos cuyo tipo está definido por el typename *T*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)