---
title: "StringReference::StringReference (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::StringReference"
dev_langs: 
  - "C++"
ms.assetid: 87dd9201-e638-4913-b37c-7091ae3f91ea
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# StringReference::StringReference (Constructor)
Inicializa una nueva instancia de la clase `StringReference`.  
  
## Sintaxis  
  
```cpp  
  
    StringReference();  
  
   StringReference(const StringReference& __fstrArg)  
  
StringReference(const ::default::char16* __strArg)  
  
StringReference(const ::default::char16* __strArg, size_t __lenArg)  
```  
  
#### Parámetros  
 `__fstrArg`  
 `StringReference` cuyos datos se usan para inicializar la nueva instancia.  
  
 `__strArg`  
 Puntero a una matriz de valores char16 que se emplea para inicializar la nueva instancia.  
  
 `__lenArg`  
 Número de elementos de `__strArg`.  
  
## Comentarios  
 La primera versión de este constructor es el constructor predeterminado. La segunda versión inicializa una nueva clase de instancia `StringReference` desde el objeto especificado por el parámetro `__fstrArg`. La tercera y la cuarta sobrecargas inicializan una nueva instancia de `StringReference` desde una matriz de valores char16. char16 representa un carácter de texto UNICODE de 16 bits.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::StringReference \(Clase\)](../cppcx/platform-stringreference-class.md)