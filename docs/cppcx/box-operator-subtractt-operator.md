---
title: "Operador Box::operator T | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator T"
dev_langs: 
  - "C++"
ms.assetid: 7445ef5b-563c-4ff0-829d-f22aa558b5ec
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador Box::operator T
Permite conversiones boxing de una clase de valor `T` o de una clase `enum``T` en `Box<T>`.  
  
## Sintaxis  
  
```cpp  
operator Box<T>^(T valueType);  
```  
  
#### Parámetros  
 `T`  
 Cualquier tipo de enumeración, clase de valor o struct de valor. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
## Valor devuelto  
 Instancia de `Platform::Box<T>``^` que representa el valor original convertido en una clase ref mediante una conversión boxing.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Platform::Box \(Clase\)](../cppcx/platform-box-class.md)   
 [Platform::IBox \(Interfaz\)](../cppcx/platform-ibox-interface.md)   
 [Conversión boxing](../cppcx/boxing-c-cx.md)