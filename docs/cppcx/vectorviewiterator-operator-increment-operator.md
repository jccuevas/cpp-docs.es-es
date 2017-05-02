---
title: "VectorViewIterator::operator++ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator++ (Operador)"
ms.assetid: 5391e6e2-a7ee-4dab-8cee-b2237894246f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator++ (Operador)
Incrementa el objeto VectorViewIterator actual.  
  
## Sintaxis  
  
```  
  
VectorViewIterator& operator++();  
VectorViewIterator operator++(  
   int  
);  
```  
  
## Valor devuelto  
 La primera sintaxis incrementa y devuelve después el objeto VectorViewIterator actual. La segunda sintaxis devuelve una copia del objeto VectorViewIterator actual e incrementa después el objeto VectorViewIterator actual.  
  
## Comentarios  
 La primera sintaxis de VectorViewIterator incrementa previamente el objeto VectorViewIterator actual.  
  
 La segunda sintaxis incrementa posteriormente el objeto VectorViewIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorViewIterator \(Clase\)](../cppcx/platform-collections-vectorviewiterator-class.md)