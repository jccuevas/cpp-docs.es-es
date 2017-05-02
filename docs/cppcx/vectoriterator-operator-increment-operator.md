---
title: "VectorIterator::operator++ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator++ (Operador)"
ms.assetid: c46b18ff-45be-436a-8f31-b3a5ecc19b77
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator++ (Operador)
Incrementa el objeto VectorIterator actual.  
  
## Sintaxis  
  
```  
  
VectorIterator& operator++();  
VectorIterator operator++(  
   int  
);  
```  
  
## Valor devuelto  
 La primera sintaxis incrementa y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual e incrementa después el objeto VectorIterator actual.  
  
## Comentarios  
 La primera sintaxis de VectorIterator incrementa previamente el objeto VectorIterator actual.  
  
 La segunda sintaxis incrementa posteriormente el objeto VectorIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)