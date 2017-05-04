---
title: "String::IsFastPass (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::String::IsFastPass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::String::IsFastPass"
ms.assetid: 0a8c2db7-e44f-45fe-9570-3dc82fbbacdd
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# String::IsFastPass (M&#233;todo)
Indica si el objeto String actual participa en una operación *rápida de paso*. En una operación rápida de paso, se suspende el recuento de referencias.  
  
## Sintaxis  
  
```cpp  
  
bool IsFastPass();  
```  
  
## Valor devuelto  
 Es `true` si el objeto String actual es de paso rápido; de lo contrario, es `false`.  
  
## Comentarios  
 En una llamada a una función donde un objeto con recuento de referencias es un parámetro y la función llamada solo lee ese objeto, el compilador puede suspender de forma segura el recuento de referencias y mejorar el rendimiento de la llamada. El código no puede hacer nada útil con esta propiedad. El sistema controla todos los detalles.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** vccorlib.h  
  
## Vea también  
 [Platform::String \(Clase\)](../cppcx/platform-string-class.md)