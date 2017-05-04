---
title: "WriteOnlyArray::set (Funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::WriteOnlyArray::set"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WriteOnlyArray::set (Función)"
ms.assetid: 0359f922-f25e-47d1-b7df-87e7fd0f76e5
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# WriteOnlyArray::set (Funci&#243;n)
Establece el valor especificado en el índice especificado de la matriz.  
  
## Sintaxis  
  
```cpp  
T& set(  
   unsigned int indexArg,  
   T valueArg);  
```  
  
#### Parámetros  
 `indexArg`  
 Índice del elemento que se va a establecer.  
  
 `valueArg`  
 El valor que se va a establecer en `indexArg`.  
  
## Valor devuelto  
 Una referencia al elemento que se acaba de establecer.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Platform  
  
## Vea también  
 [Platform::WriteOnlyArray \(Clase\)](../cppcx/platform-writeonlyarray-class.md)   
 [Array y WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)