---
title: "VectorViewIterator::operator!= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator!= (Operador)"
ms.assetid: 00d55da7-9d85-495b-baaa-b5cdfa81aa7d
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator!= (Operador)
Indica si el objeto VectorViewIterator actual no es igual que un objeto VectorViewIterator especificado.  
  
## Sintaxis  
  
```  
bool operator!=(  
   const VectorViewIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro VectorViewIterator.  
  
## Valor devuelto  
 `true` si el objeto VectorViewIterator actual es igual a `other`; de lo contrario, es `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)