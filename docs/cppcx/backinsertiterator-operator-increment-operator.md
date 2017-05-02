---
title: "BackInsertIterator::operator++ (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator++ (Operador)"
ms.assetid: 08324574-db2b-4d95-825e-a93a56f327da
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator++ (Operador)
Devuelve una referencia al objeto BackInsertIterator actual. El iterador no se modifica.  
  
## Sintaxis  
  
```  
  
BackInsertIterator& operator++();  
  
BackInsertIterator operator++(  
   int  
);  
```  
  
## Valor devuelto  
 Referencia al objeto BackInsertIterator actual.  
  
## Comentarios  
 Por diseño, el primero ejemplo de sintaxis incrementa previamente el objeto BackInsertIterator actual y el segundo lo incrementa posteriormente. El tipo `int` de la segunda sintaxis indica una operación de incremento posterior, no un operando entero real.  
  
 Sin embargo, este operador no modifica realmente el objeto BackInsertIterator. En su lugar, este operador devuelve una referencia al iterador actual sin modificar. Este comportamiento es el mismo que el de [operator\*](../cppcx/backinsertiterator-operator-dereference-operator.md).  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::BackInsertIterator \(Clase\)](../cppcx/platform-collections-backinsertiterator-class.md)