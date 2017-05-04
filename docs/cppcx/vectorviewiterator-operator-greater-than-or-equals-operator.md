---
title: "VectorViewIterator::operator&gt;= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator>= (Operador)"
ms.assetid: 506fbf12-a28f-4695-a5a4-418341dec806
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&gt;= (Operador)
Indica si el objeto VectorViewIterator actual es mayor o igual que el objeto VectorViewIterator especificado.  
  
## Sintaxis  
  
```  
  
bool operator>=(  
   const VectorViewIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro VectorViewIterator.  
  
## Valor devuelto  
 `true` si el objeto VectorViewIterator actual es mayor o igual que `other`; en caso contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)