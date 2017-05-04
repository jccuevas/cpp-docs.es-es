---
title: "VectorIterator::operator!= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator!= (Operador)"
ms.assetid: 88b71c7e-9c88-4282-a518-455059da16c2
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator!= (Operador)
Indica si el objeto VectorIterator actual no es igual que un objeto VectorIterator especificado.  
  
## Sintaxis  
  
```  
bool operator!=(  
   const VectorIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
## Valor devuelto  
 Es `true` si el objeto VectorIterator actual no es igual que `other`; de lo contrario, es `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)