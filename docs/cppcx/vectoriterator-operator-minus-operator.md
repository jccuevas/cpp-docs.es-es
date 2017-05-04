---
title: "VectorIterator::operator- (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator- (Operador)"
ms.assetid: 5714c132-e973-47fd-901b-ba13da7b9372
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator- (Operador)
Resta un número especificado de elementos del iterador actual produciendo un nuevo iterador, o un iterador especificado del iterador actual produciendo el número de elementos entre los iteradores.  
  
## Sintaxis  
  
```  
  
VectorIterator operator-(  
   difference_type n  
) const;  
  
difference_type operator-(  
   const VectorIterator& other  
) const;  
```  
  
#### Parámetros  
 `n`  
 Número de elementos.  
  
 `other`  
 Otro objeto VectorIterator.  
  
## Valor devuelto  
 La sintaxis del primer operador devuelve un objeto VectorIterator que tiene `n` elementos menos que el objeto VectorIterator actual. La segunda sintaxis del operador devuelve el número de elementos que hay entre el objeto actual y `other` VectorIterator.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)