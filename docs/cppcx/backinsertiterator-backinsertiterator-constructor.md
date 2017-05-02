---
title: "BackInsertIterator::BackInsertIterator (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::BackInsertIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::BackInsertIterator (Constructor)"
ms.assetid: ae6f0213-a7bb-43b8-9a5e-7a8dad7c76f8
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::BackInsertIterator (Constructor)
Inicializa una nueva instancia de la clase `BackInsertIterator`.  
  
## Sintaxis  
  
```  
  
explicit BackInsertIterator(  
   Windows::Foundation::Collections::IVector<T>^ v  
);  
```  
  
#### Parámetros  
 `v`  
 Objeto IVector\<T\>.  
  
## Comentarios  
 Un objeto `BackInsertIterator` inserta elementos a continuación del último elemento del objeto especificado por el parámetro `v`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::BackInsertIterator \(Clase\)](../cppcx/platform-collections-backinsertiterator-class.md)