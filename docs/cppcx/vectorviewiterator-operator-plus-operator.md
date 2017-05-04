---
title: "VectorViewIterator::operator+ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator+ (Operador)"
ms.assetid: 8206de2f-61b3-49cd-9715-d57695d880b3
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator+ (Operador)
Devuelve un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator especificado.  
  
## Sintaxis  
  
```  
  
VectorViewIterator operator+(  
   difference_type n  
) const;  
  
template <  
   typename T  
>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i  
);  
  
```  
  
#### Parámetros  
 `T`  
 En la segunda sintaxis, el typename del objeto VectorViewIterator.  
  
 `n`  
 Desplazamiento entero.  
  
 `i`  
 En la segunda sintaxis, un objeto VectorViewIterator.  
  
## Valor devuelto  
 En la primera sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorViewIterator actual.  
  
 En la segunda sintaxis, un objeto VectorViewIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)