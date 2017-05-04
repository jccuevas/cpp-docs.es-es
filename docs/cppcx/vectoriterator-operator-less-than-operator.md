---
title: "VectorIterator::operator&lt; (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator< (Operador)"
ms.assetid: 1d7dabdd-70da-4c39-b76e-e22e743751a0
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator&lt; (Operador)
Indica si el objeto VectorIterator actual es menor que un objeto VectorIterator especificado.  
  
## Sintaxis  
  
```cpp  
  
bool operator<(  
   const VectorIterator& other  
) const   
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
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)