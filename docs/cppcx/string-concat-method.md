---
title: "String::Concat (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::Concat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::Concat"
ms.assetid: 68052d22-3df0-4777-828d-fc3a8e8a3ab7
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::Concat (M&#233;todo)
Concatena los valores de dos objetos String.  
  
## Sintaxis  
  
```cpp  
  
String^ Concat( String ^ str1,   
String ^ str2  
)  
  
```  
  
#### Parámetros  
 `str1`  
 El primer objeto String o `null`.  
  
 `str2`  
 El segundo objeto String o `null`.  
  
## Valor devuelto  
 Un nuevo objeto String^ cuyo valor es la concatenación de los valores de `str1` y `str2`.  
  
 Si `str1` es `null` y `str2` no lo es, se devuelve `str1` . Si `str2` es `null` y `str1` no lo es, se devuelve `str2`. Si `str1` y `str2` son ambos `null`, se devuelve la cadena vacía \(L""\).  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)