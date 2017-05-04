---
title: "VectorIterator::operator&lt;= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator<= (Operador)"
ms.assetid: 57d3c269-77a5-4731-a3b4-dcda2758da19
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator&lt;= (Operador)
Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.  
  
## Sintaxis  
  
```cpp  
  
bool operator<=(  
   const VectorIterator& other  
) const   
```  
  
#### Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
## Valor devuelto  
 `true` si el objeto VectorIterator actual es menor o igual que `other`; en caso contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)