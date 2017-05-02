---
title: "String::Data (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Data"
ms.assetid: 9be4e015-dfb8-431e-a252-8498bd833f03
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Data (M&#233;todo)
Devuelve un puntero al principio del búfer de datos del objeto como una matriz de estilo C de elementos `char16` \(`wchar_t`\).  
  
## Sintaxis  
  
```  
const char16* Data()  
```  
  
## Valor devuelto  
 Puntero al principio de una matriz `const` `char16` de caracteres Unicode \(`char16` es una definición de tipos para `wchar_t`\).  
  
## Comentarios  
 Usa este método para convertir de `Platform::String^` a `wchar_t*`. Cuando el objeto `String` sale del ámbito, ya no se garantiza que el puntero a datos sea válido. Para almacenar los datos más allá de la duración del objeto `String` original, usa [wcscpy\_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) para copiar la matriz a la memoria que has asignado.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)   
 [String::Begin \(Método\)](../cppcx/string-begin-method.md)