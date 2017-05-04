---
title: "WriteOnlyArray::begin (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::begin"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::begin (Método)"
ms.assetid: 25025fa0-8f55-4abf-93ad-71db45ddfae3
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::begin (M&#233;todo)
Devuelve un puntero al primer elemento de la matriz.  
  
## Sintaxis  
  
```cpp  
T* begin() const;  
```  
  
## Valor devuelto  
 Puntero al primer elemento de la matriz.  
  
## Comentarios  
 Este iterador se puede usar con los algoritmos de STL como `std::sort` para operar en elementos de la matriz.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Platform  
  
## Vea también  
 [Platform::WriteOnlyArray \(Clase\)](../cppcx/platform-writeonlyarray-class.md)   
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)