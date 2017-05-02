---
title: "Platform::Box (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::Box"
dev_langs: 
  - "C++"
ms.assetid: b3d7ea37-e98a-4fbc-80b0-ad35e50250c6
caps.latest.revision: 7
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 7
---
# Platform::Box (Clase)
Habilita un tipo de valor como `Windows::Foundation::DateTime` o un tipo escalar como `int` para almacenarlo en un tipo `Platform::Object`. Normalmente no es necesario usar `Box` explícitamente porque la conversión boxing se produce de manera implícita cuando se convierte un tipo de valor a `Object^`.  
  
## Sintaxis  
  
```cpp  
ref class Box abstract;  
```  
  
## Comentarios  
  
## Requisitos  
 **Encabezado:** vccorlib.h  
  
 **Espacio de nombres:** Plataforma  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)   
 [Conversión boxing](../cppcx/boxing-c-cx.md)