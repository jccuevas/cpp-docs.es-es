---
title: "Object::ReferenceEquals (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "02/09/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Object::ReferenceEquals"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Plataforma, Object::ReferenceEquals"
ms.assetid: a179e74a-46c7-4bfd-b848-b89ef3ff7197
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Object::ReferenceEquals (M&#233;todo)
Determina si las instancias de Object especificadas son la misma instancia.  
  
## Sintaxis  
  
```cpp  
public:static bool ReferenceEquals(  Object^ obj1,   Object^ obj2)  
```  
  
## Parámetros  
 obj1  
 Primer objeto que se va a comparar.  
  
 obj2  
 Segundo objeto que se va a comparar.  
  
## Valor devuelto  
 `true` si los dos objetos son iguales; de lo contrario, `false`.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Encabezado:** vccorlib.h  
  
## Vea también  
 [Platform::Object \(Clase\)](../cppcx/platform-object-class.md)