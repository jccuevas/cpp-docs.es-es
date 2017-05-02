---
title: "ArrayReference::operator= (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operator="
dev_langs: 
  - "C++"
ms.assetid: 131a4612-d66b-48e4-90af-c665ccc0cce4
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# ArrayReference::operator= (Operador)
Asigna el objeto especificado al objeto [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) actual mediante semántica de transferencia de recursos.  
  
## Sintaxis  
  
```cpp  
  
ArrayReference& operator=(ArrayReference&& __otherArg);  
  
```  
  
#### Parámetros  
 `__ otherArg`  
 Objeto que se mueve al objeto `ArrayReference` actual.  
  
## Valor devuelto  
 Referencia a un objeto de tipo `ArrayReference`.  
  
## Comentarios  
 `Platform::ArrayReference` es una plantilla de clase estándar de C\+\+, no una clase de referencia.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::ArrayReference \(Clase\)](../cppcx/platform-arrayreference-class.md)