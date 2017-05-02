---
title: "Vector::InsertAt (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::InsertAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::InsertAt"
ms.assetid: 05b2ca08-234e-4fc0-acfd-cafa148d1577
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::InsertAt (M&#233;todo)
Inserta el elemento especificado en el objeto Vector actual detrás del elemento identificado por el índice especificado.  
  
## Sintaxis  
  
```  
  
virtual void InsertAt(  
   unsigned int index,   
   T item)  
```  
  
#### Parámetros  
 `index`  
 Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.  
  
 `item`  
 Elemento que se va a insertar en el objeto Vector detrás del elemento especificado por `index`. El tipo de `item` se define mediante el typename *T*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)