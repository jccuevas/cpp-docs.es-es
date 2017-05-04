---
title: "VectorViewIterator::operator&gt; (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator> (Operador)"
ms.assetid: c689b677-e3c6-4f6e-8e3a-54d5f2a6123d
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&gt; (Operador)
Indica si el objeto VectorViewIterator actual es mayor que un objeto VectorViewIterator especificado.  
  
## Sintaxis  
  
```  
  
bool operator>(  
   const VectorViewIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro VectorViewIterator.  
  
## Valor devuelto  
 `true` si el objeto VectorViewIterator actual es mayor que `other`; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)