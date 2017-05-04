---
title: "Operador StringReference::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::StringReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 03a33467-d65f-4508-bcb4-17d7cc99398f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador StringReference::operator=
Asigna el objeto especificado al objeto `StringReference` actual.  
  
## Sintaxis  
  
```cpp  
  
   StringReference& operator=(const StringReference& __fstrArg);  
  
StringReference& operator=(const ::default::char16* __strArg);  
  
```  
  
#### Parámetros  
 `__fstrArg`  
 Dirección de un objeto `StringReference` que se usa para inicializar el objeto `StringReference` actual.  
  
 `__strArg`  
 Puntero a una matriz de valores char16 que se usa para inicializar el objeto `StringReference` actual.  
  
## Valor devuelto  
 Referencia a un objeto de tipo `StringReference`.  
  
## Comentarios  
 Como `StringReference` es una clase estándar de C\+\+ y no una clase de referencia, no aparece en el **Examinador de objetos**.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::StringReference \(Clase\)](../cppcx/platform-stringreference-class.md)