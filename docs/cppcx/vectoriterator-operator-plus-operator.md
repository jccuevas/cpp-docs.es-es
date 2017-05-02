---
title: "VectorIterator::operator+ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator+ (Operador)"
ms.assetid: 5e907537-7d10-4766-a412-e7ea08b3456a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator+ (Operador)
Devuelve un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator especificado.  
  
## Sintaxis  
  
```  
  
VectorIterator operator+(  
   difference_type n) ;  
  
template <  
   typename T  
>  
inline VectorIterator<T> operator+(  
   ptrdiff_t n,  
   const VectorIterator<T>& i  
);  
  
```  
  
#### Parámetros  
 `T`  
 En la segunda sintaxis, el typename del objeto VectorIterator.  
  
 `n`  
 Desplazamiento entero.  
  
 `i`  
 En la segunda sintaxis, un objeto VectorIterator.  
  
## Valor devuelto  
 En la primera sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el objeto VectorIterator actual.  
  
 En la segunda sintaxis, un objeto VectorIterator que hace referencia al elemento en el desplazamiento especificado desde el principio del parámetro `i`.  
  
## Comentarios  
 El ejemplo de la primera sintaxis  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Espacio de nombres de plataforma \(NOTINBUILD\)](http://msdn.microsoft.com/es-es/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)