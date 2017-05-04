---
title: "Platform::ValueType (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::ValueType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::ValueType (Clase)"
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 2
---
# Platform::ValueType (Clase)
La clase base para las instancias de tipos de valor.  
  
## Sintaxis  
  
```cpp  
public ref class ValueType : Object  
```  
  
## Comentarios  
 La clase ValueType se usa para construir tipos de valor. ValueType se deriva de Object, que tiene miembros básicos. Sin embargo, el compilador desasocia esos miembros básicos de los tipos de valor que se derivan de la clase ValueType. El compilador vuelve a asociar esos miembros básicos cuando se encuadra un tipo de valor.  
  
## Requisitos  
 **Cliente mínimo admitido:** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **Servidor mínimo admitido:** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **Espacio de nombres:** Platform  
  
 **Metadatos:** platform.winmd  
  
## Vea también  
 [Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)