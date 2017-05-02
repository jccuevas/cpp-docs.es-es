---
title: "VectorViewIterator::operator- (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator- (Operador)"
ms.assetid: 03935872-8acc-4919-ae14-f375ca738aac
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator- (Operador)
Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.  
  
## Sintaxis  
  
```  
  
VectorViewIterator operator-(  
   difference_type n  
) const;  
  
difference_type operator-(  
   const VectorViewIterator& other  
) const;  
```  
  
#### Parámetros  
 `n`  
 Número de elementos.  
  
 `other`  
 Otro VectorViewIterator.  
  
## Valor devuelto  
 La sintaxis del primer operador devuelve un objeto VectorViewIterator que tiene `n` elementos menos que el objeto VectorViewIterator actual. La segunda sintaxis del operador devuelve el número de elementos que hay entre el objeto actual y `other` VectorViewIterator.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)