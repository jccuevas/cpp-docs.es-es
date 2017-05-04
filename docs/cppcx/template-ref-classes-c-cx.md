---
title: "Clases ref de plantilla (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 15
---
# Clases ref de plantilla (C++/CX)
Las plantillas de C\+\+ no se publican para metadatos y, por consiguiente, no pueden tener accesibilidad pública ni protegida en tu programa. Puedes, por supuesto, utilizar las plantillas de C\+\+ estándar internamente en tu programa. Además, puedes definir una clase ref privada como plantilla y puedes declarar una clase ref de plantilla especializada de forma explícita como miembro privado de una clase ref pública.  
  
## Crear plantillas de clase ref  
 En el ejemplo siguiente se muestra cómo declarar una clase ref privada como plantilla y también cómo declarar una plantilla de C\+\+ estándar, y cómo declarar ambas como miembros de una clase ref pública. Observa que la plantilla de C\+\+ estándar se puede especializar mediante un tipo de [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)], en este caso un objeto Platform::String^.  
  
 [!code-cpp[cx_templates#01](../snippets/cpp/VS_Snippets_Misc/cx_templates/cpp/class1.h#01)]  
  
## Vea también  
 [Sistema de tipos \(C\+\+\/CX\)](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje Visual C\+\+](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)