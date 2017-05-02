---
title: "String::operator== (Operador) (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator=="
ms.assetid: c804b269-64f9-4bc0-929b-2dfa87bf46ac
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator== (Operador) (C++/CX)
Indica si dos objetos String especificados tienen el mismo valor de texto.  
  
## Sintaxis  
  
```cpp  
  
bool String::operator==( String^ str1,  
                         String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String que se va a comparar.  
  
 `str2`  
 El segundo objeto String que se va a comparar.  
  
## Valor devuelto  
 Es `true` si el contenido de `str1` es igual a `str2`; si no, es `false`.  
  
## Comentarios  
 Este operador es equivalente a [String::CompareOrdinal \(Método\)](../cppcx/string-compareordinal-method.md).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)