---
title: "Vector::GetMany (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetMany (Método)"
ms.assetid: e2d5ccf4-101a-47e5-a0d8-56f65a7ff28d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetMany (M&#233;todo)
Recupera una secuencia de elementos del objeto Vector actual, empezando en el índice especificado, y los copia en la matriz asignada por el llamador.  
  
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
 Matriz de elementos asignada por el llamador que empieza con el elemento especificado por `startIndex` y termina con el último elemento del objeto Vector.  
  
## Valor devuelto  
 Número de elementos recuperados.  
  
## Comentarios  
 Esta función no se ha diseñado para el uso en el código de cliente. Se usa internamente en la [función to\_vector](../cppcx/to-vector-function.md) para habilitar la conversión eficaz de instancias Platform::Vector a instancias std::vector.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Vector \(Clase\)](../cppcx/platform-collections-vector-class.md)