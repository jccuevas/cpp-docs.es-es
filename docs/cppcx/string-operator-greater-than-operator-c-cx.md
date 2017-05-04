---
title: "String::operator&gt; (Operador) (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator>"
ms.assetid: d32ad538-b992-4487-a1d3-ad7ba84dbdff
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator&gt; (Operador) (C++/CX)
Indica si el valor de un objeto String es mayor que el valor de un segundo objeto String.  
  
## Sintaxis  
  
```cpp  
  
bool String::operator>( String^ str1,  
                         String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String.  
  
 `str2`  
 El segundo objeto String.  
  
## Valor devuelto  
 Es `true` si el valor de `str1` es mayor que el valor de `str2`; en caso contrario, es `false`.  
  
## Comentarios  
 Este operador es equivalente a llamar explícitamente a [String::CompareOrdinal](../cppcx/string-compareordinal-method.md) y obtener un resultado mayor que cero.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)