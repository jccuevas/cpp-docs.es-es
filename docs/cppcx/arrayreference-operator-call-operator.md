---
title: "Operador ArrayReference::operator() | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vccorlib/Platform::ArrayReference::operatorArray^"
dev_langs: 
  - "C++"
ms.assetid: 48726344-82bb-4c1d-b246-ed74b895f99b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador ArrayReference::operator()
Vuelve a convertir el objeto [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) actual a una clase [Platform::Array](../cppcx/platform-array-class.md).  
  
## Sintaxis  
  
```cpp  
  
Array<__TArg>^ operator ();  
  
```  
  
## Valor devuelto  
 Identificador a objeto de tipo `Array<__TArg>^`.  
  
## Comentarios  
 [Platform::ArrayReference](../cppcx/platform-arrayreference-class.md) y [Platform::Array](../cppcx/platform-array-class.md) son plantillas de clase estándar de C\+\+, no clases de referencia.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::ArrayReference \(Clase\)](../cppcx/platform-arrayreference-class.md)