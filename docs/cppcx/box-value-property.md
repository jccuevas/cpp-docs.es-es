---
title: "Box::Value (Propiedad) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box::Value"
dev_langs: 
  - "C++"
ms.assetid: f456b105-6c14-4737-8c27-ad47d1eabd32
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Box::Value (Propiedad)
Devuelve el valor encapsulado en el objeto `Box`.  
  
## Sintaxis  
  
```cpp  
virtual property T Value{  
   T get();  
}  
```  
  
## Valor devuelto  
 Devuelve el valor al que se le ha aplicado la conversión boxing con el mismo tipo que tenía originalmente antes de que se le aplicara esa conversión.  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Platform::Box \(Clase\)](../cppcx/platform-box-class.md)   
 [Conversión boxing](../cppcx/boxing-c-cx.md)