---
title: "Operador Box::operator Box&lt;const volatile T&gt;^ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<const volatile T>^"
dev_langs: 
  - "C++"
ms.assetid: 3c91cf0f-1e90-4daf-8468-a7d8aedb6784
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador Box::operator Box&lt;const volatile T&gt;^
Permite conversiones boxing de una clase de valor `const volatile``T` o de un tipo `enum``T` en `Box<T>`.  
  
## Sintaxis  
  
```cpp  
operator Box<const volatile T>^(const volatile T valueType);  
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