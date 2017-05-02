---
title: "VectorView::IndexOf (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::IndexOf (Método)"
ms.assetid: 848117ec-ad4a-4a0b-9c1e-9076e5188869
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::IndexOf (M&#233;todo)
Busca el elemento especificado en el objeto VectorView actual y, si lo encuentra, devuelve el índice del elemento.  
  
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
  
 El parámetro `index` es 0 si el elemento es el primer elemento del objeto VectorView o no se encuentra el elemento. Si el valor devuelto es `true`, se encontró el elemento y es el primer elemento; de lo contrario, no se encuentra el elemento.  
  
## Valor devuelto  
 `true` si se encontró el elemento especificado; de lo contrario, `false`.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [VectorView Class](http://msdn.microsoft.com/es-es/79697692-ae58-40e0-958f-cf1be6347994)