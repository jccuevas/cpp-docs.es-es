---
title: "String::String (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::String"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::String"
ms.assetid: 80b6461a-5b12-4dcb-9323-f2c5f310bbc6
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::String (Constructor)
Inicializa una nueva instancia de la clase String con una copia de los datos de la cadena de entrada.  
  
## Sintaxis  
  
```cpp  
  
String();  
  
String(  
  char16* s  
)  
  
String(  
  char16* s,   
  unsigned int n  
)  
```  
  
## Parámetros  
 `s`  
 Serie de caracteres anchos que inicializan la cadena. char16  
  
 `n`  
 Un número que especifica la longitud de la cadena.  
  
## Comentarios  
 Si el rendimiento es crítico y controla la vigencia de la cadena de origen, puede utilizar [Platform::StringReference](../cppcx/platform-stringreference-class.md) en lugar de String.  
  
## Ejemplo  
  
```  
String^ s = L”Hello!”;  
```  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)