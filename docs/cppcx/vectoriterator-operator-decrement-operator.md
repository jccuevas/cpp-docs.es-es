---
title: "VectorIterator::operator-- (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator--"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-- (Operador)"
ms.assetid: 650a3037-2984-4110-9d7c-cd3756e5f4b9
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-- (Operador)
Disminuye el objeto VectorIterator actual.  
  
## Sintaxis  
  
```  
  
VectorIterator& operator--();  
VectorIterator operator--(  
   int  
);  
```  
  
## Valor devuelto  
 La primera sintaxis disminuye y devuelve después el objeto VectorIterator actual. La segunda sintaxis devuelve una copia del objeto VectorIterator actual y disminuye después el objeto VectorIterator actual.  
  
## Comentarios  
 La primera sintaxis de VectorIterator disminuye previamente el objeto VectorIterator actual.  
  
 La segunda sintaxis disminuye posteriormente el objeto VectorIterator actual. El tipo `int` de la segunda sintaxis indica una operación de decremento posterior, no un operando entero real.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::VectorIterator \(Clase\)](../cppcx/platform-collections-vectoriterator-class.md)