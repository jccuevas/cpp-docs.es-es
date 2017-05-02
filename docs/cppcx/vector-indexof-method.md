---
title: "Vector::IndexOf (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::IndexOf (Método)"
ms.assetid: 4a965992-3858-4e3f-992a-b94c0580b2f7
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::IndexOf (M&#233;todo)
Busca el elemento especificado en el objeto Vector actual y, si lo encuentra, devuelve el índice del elemento.  
  
## Sintaxis  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
#### Parámetros  
 `value`  
 El elemento que se va a buscar.  
  
 `index`  
 El índice de base cero del elemento si se encuentra el parámetro `value`; en caso contrario, 0.  
  
 El parámetro `index` es 0 si el elemento es el primer elemento del objeto Vector o no se encuentra el elemento. Si el valor devuelto es `true`, se encontró el elemento y es el primer elemento; de lo contrario, no se encuentra el elemento.  
  
## Valor devuelto  
 `true` si se encontró el elemento especificado; de lo contrario, `false`.  
  
## Comentarios  
 IndexOf utiliza std::find\_if para buscar el elemento. Por tanto, los tipos de elementos personalizados deben sobrecargar los operadores \=\= y \!\= para habilitar las comparaciones de igualdad que requiere find\_if.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)