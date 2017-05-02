---
title: "String::Equals (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Equals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Equals"
ms.assetid: b0c78419-242d-4d38-93e3-ff2818412624
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Equals (M&#233;todo)
Indica si el objeto String especificado tiene el mismo valor que el objeto actual.  
  
## Sintaxis  
  
```cpp  
  
bool String::Equals(Object^ str);  
  
bool String::Equals(String^ str);  
  
```  
  
#### Parámetros  
 `str`  
 Objeto que se va a comparar.  
  
## Valor devuelto  
 `true` si `str` es igual al objeto actual; en caso contrario, `false`.  
  
## Comentarios  
 Este método equivale a [String::CompareOrdinal \(Método\)](../cppcx/string-compareordinal-method.md). En la primera sobrecarga, se espera que el parámetro `str` se pueda convertir en un objeto String^.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)