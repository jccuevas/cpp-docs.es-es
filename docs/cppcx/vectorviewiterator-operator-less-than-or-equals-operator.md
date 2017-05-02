---
title: "VectorViewIterator::operator&lt;= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator<="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator<= (Operador)"
ms.assetid: 523bf6ca-fb45-498b-8e94-fa8a093dd4ad
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&lt;= (Operador)
Indica si el objeto VectorIterator actual es menor o igual que un objeto VectorIterator especificado.  
  
## Sintaxis  
  
```  
  
bool operator<=(  
   const VectorViewIterator& other  
) const;  
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
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)