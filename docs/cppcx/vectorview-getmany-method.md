---
title: "VectorView::GetMany (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetMany (Método)"
ms.assetid: 67d9348f-66fe-417e-9e25-5de0a3cd306c
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetMany (M&#233;todo)
Recupera una secuencia de elementos del objeto VectorView actual, empezando en el índice especificado.  
  
## Sintaxis  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
#### Parámetros  
 `startIndex`  
 Índice basado en cero del principio de los elementos que se van a recuperar.  
  
 `dest`  
 Cuando se completa esta operación, matriz de elementos que empieza con el elemento especificado por `startIndex` y termina con el último elemento del objeto VectorView.  
  
## Valor devuelto  
 Número de elementos recuperados.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [VectorView Class](http://msdn.microsoft.com/es-es/79697692-ae58-40e0-958f-cf1be6347994)