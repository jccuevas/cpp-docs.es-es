---
title: "Vector::SetAt (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::SetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::SetAt"
ms.assetid: ddfb454e-dbfd-4831-b040-674b085d8fb6
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::SetAt (M&#233;todo)
Asigna el valor especificado al elemento del objeto Vector actual identificado por el índice especificado.  
  
## Sintaxis  
  
```  
  
virtual void SetAt(  
   unsigned int index,   
   T item  
);  
```  
  
#### Parámetros  
 `index`  
 Entero sin signo de base cero que especifica un elemento determinado en el objeto Vector.  
  
 `item`  
 El valor que se va a asignar al elemento especificado. El tipo de `item` se define mediante el typename *T*.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)