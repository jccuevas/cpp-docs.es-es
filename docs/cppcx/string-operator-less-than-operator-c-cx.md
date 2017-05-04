---
title: "String::operator&lt; (Operador) (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator<"
ms.assetid: 94221597-70dd-4456-a084-5bd2b8fa7723
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator&lt; (Operador) (C++/CX)
Indica si el valor de un objeto String es menor que el valor de un segundo objeto String.  
  
## Sintaxis  
  
```cpp  
  
bool String::operator<( String^ str1,  
                         String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String.  
  
 `str2`  
 El segundo objeto String.  
  
## Valor devuelto  
 Es `true` si el valor de `str1` es menor que el valor de `str2`; en caso contrario, es `false`.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)