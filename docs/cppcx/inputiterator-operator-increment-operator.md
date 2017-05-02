---
title: "InputIterator::operator++ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator++ (Operador)"
ms.assetid: 50781585-7a12-4f02-bff8-68fe0adf0693
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator++ (Operador)
Incrementa el objeto InputIterator actual.  
  
## Sintaxis  
  
```  
  
InputIterator& operator++();  
  
InputIterator operator++(  
   int  
);  
```  
  
## Valor devuelto  
 La primera sintaxis incrementa y devuelve después el objeto InputIterator actual. La segunda sintaxis devuelve una copia del objeto InputIterator actual e incrementa después el objeto InputIterator actual.  
  
## Comentarios  
 Lo primera sintaxis de InputIterator incrementa previamente el objeto InputIterator actual.  
  
 La segunda sintaxis incrementa posteriormente el objeto InputIterator actual. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::InputIterator \(Clase\)](../cppcx/platform-collections-inputiterator-class.md)