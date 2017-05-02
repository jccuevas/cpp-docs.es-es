---
title: "VectorViewIterator::operator&lt; (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator< (Operador)"
ms.assetid: 411c9af9-78b1-4b1b-839b-3bec76020184
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&lt; (Operador)
Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.  
  
## Sintaxis  
  
```  
bool operator<(  
   const VectorViewIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro objeto VectorIterator.  
  
## Valor devuelto  
 Es `true` si el objeto VectorIterator actual es menor que `other`; de lo contrario, es `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)