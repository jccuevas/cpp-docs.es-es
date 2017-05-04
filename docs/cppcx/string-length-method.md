---
title: "String::Length (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Length"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Length"
ms.assetid: 92376897-1bf2-4b7a-9298-d2d3f05d8d6b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Length (M&#233;todo)
Recupera el número de caracteres del objeto String actual.  
  
## Sintaxis  
  
```cpp  
  
unsigned int Length()  
```  
  
## Valor devuelto  
 Número de caracteres del objeto String actual.  
  
## Comentarios  
 La longitud de un objeto String sin caracteres es cero. La longitud de la cadena siguiente es 5:  
  
```  
  
String^ str = "Hello";  
int len = str->Length(); //len = 5  
```  
  
 La matriz de caracteres devuelta por [String::Data \(Método\)](../cppcx/string-data-method.md) tiene un carácter adicional, que es el carácter NULL de terminación o '\\0'. Este carácter tiene también dos bytes de longitud.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)