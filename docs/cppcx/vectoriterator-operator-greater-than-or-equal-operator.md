---
title: "VectorIterator::operator&gt;= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator>= (Operador)"
ms.assetid: 8154015e-8da7-4381-8128-d3669eb88e16
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator&gt;= (Operador)
Indica si el objeto VectorIterator actual es mayor o igual que el objeto VectorIterator especificado.  
  
## Sintaxis  
  
```cpp  
  
bool operator>=(  
   const VectorIterator& other  
) const   
```  
  
#### Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
## Valor devuelto  
 `true` si el objeto VectorIterator actual es mayor o igual que `other`; en caso contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)