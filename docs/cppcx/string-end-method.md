---
title: "String::End (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::End"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::End"
ms.assetid: c02ad0db-d35d-45f4-9b2a-cfc76716358e
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::End (M&#233;todo)
Devuelve un puntero después del final de la cadena actual.  
  
## Sintaxis  
  
```cpp  
  
char16* End()  
```  
  
## Valor devuelto  
 Un puntero después del final de la cadena actual.  
  
## Comentarios  
 End\(\) devuelve Begin\(\)\+Length.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)