---
title: "Operador Box::operator Box&lt;volatile T&gt;^ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<volatile T>^"
dev_langs: 
  - "C++"
ms.assetid: 90fffbf6-3429-46d0-bfaf-d99b7f48de6f
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador Box::operator Box&lt;volatile T&gt;^
Permite conversiones boxing de una clase de valor `volatile``T` o de un tipo `enum``T` en `Box<T>`.  
  
## Sintaxis  
  
```cpp  
operator Box<volatile T>^(volatile T valueType);  
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