---
title: "WriteOnlyArray::end (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::end"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::end (Método)"
ms.assetid: 045045fe-f210-400b-b688-7abb95fc702a
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::end (M&#233;todo)
Devuelve un puntero a uno más allá del último elemento de la matriz.  
  
## Sintaxis  
  
```cpp  
T* end() const;  
```  
  
## Valor devuelto  
 Iterador de puntero a uno más allá del último elemento de la matriz.  
  
## Comentarios  
 Este iterador se puede usar con los algoritmos de STL para realizar operaciones como `std::sort` en elementos de la matriz.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Platform  
  
## Vea también  
 [Platform::WriteOnlyArray \(Clase\)](../cppcx/platform-writeonlyarray-class.md)   
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)