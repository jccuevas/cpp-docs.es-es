---
title: "Array::get (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::Array::get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Array::get (Método)"
ms.assetid: 3bbcd829-35e7-4912-99ba-6ab9de407287
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Array::get (M&#233;todo)
Recupera una referencia al elemento de matriz en la ubicación de índice especificada.  
  
## Sintaxis  
  
```  
  
T& get(  
unsigned int index  
)  const;  
```  
  
#### Parámetros  
 `index`  
 Un índice basado en cero que identifica un elemento de la matriz. El índice mínimo es 0 y el índice máximo es el valor especificado por el parámetro `size` en [constructor de matriz](../cppcx/array-constructors.md).  
  
## Valor devuelto  
 El elemento de matriz especificado por el parámetro `index`.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Platform::Array \(Clase\)](../cppcx/platform-array-class.md)