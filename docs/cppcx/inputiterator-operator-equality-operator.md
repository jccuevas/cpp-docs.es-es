---
title: "InputIterator::operator== (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator== (Operador)"
ms.assetid: 84f1b69a-77b9-467c-ad1a-2fe8a7c3009e
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator== (Operador)
Indica si el objeto InputIterator actual es igual que un objeto InputIterator especificado.  
  
## Sintaxis  
  
```  
bool operator==(  
   const InputIterator& other  
) const;  
```  
  
#### Parámetros  
 `other`  
 Otro objeto InputIterator.  
  
## Valor devuelto  
 `true` si el objeto InputIterator actual es igual que `other`; en caso contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::InputIterator \(Clase\)](../cppcx/platform-collections-inputiterator-class.md)