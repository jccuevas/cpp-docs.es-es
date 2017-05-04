---
title: "String::operator!= (Operador) (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::operator!="
ms.assetid: b299ea97-867e-444e-96c0-593ffac05ae0
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::operator!= (Operador) (C++/CX)
Indica si dos objetos String especificados tienen valores diferentes.  
  
## Sintaxis  
  
```cpp  
  
bool String::operator!=( String^ str1,  
                         String^ str2)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String que se va a comparar.  
  
 `str2`  
 El segundo objeto String que se va a comparar.  
  
## Valor devuelto  
 Es `true` si `str1` no es igual a `str2`; en caso contrario, es `false`.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)