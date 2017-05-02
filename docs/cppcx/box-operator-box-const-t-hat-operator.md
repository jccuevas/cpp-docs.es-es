---
title: "Operador Box::operator Box&lt;const T&gt;^ | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::operator Box<const T>^"
dev_langs: 
  - "C++"
ms.assetid: c43a2e8f-7e9d-4587-960f-1bab48923f82
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Operador Box::operator Box&lt;const T&gt;^
Permite conversiones boxing de una clase de valor `const``T` o de una clase `enum``T` en `Box<T>`.  
  
## Sintaxis  
  
```cpp  
operator Box<const T>^(const T valueType);  
```  
  
#### Parámetros  
 `T`  
 Cualquier valor de clase, struct de valor o tipo de enumeración. Incluye los tipos integrados en el [espacio de nombres predeterminado](../cppcx/default-namespace.md).  
  
## Valor devuelto  
 Instancia de `Platform::Box<T>``^` que representa el valor original convertido en una clase ref mediante una conversión boxing.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Platform::Box \(Clase\)](../cppcx/platform-box-class.md)   
 [Platform::IBox \(Interfaz\)](../cppcx/platform-ibox-interface.md)