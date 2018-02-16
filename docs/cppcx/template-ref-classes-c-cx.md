---
title: Clases ref de plantilla (C++ / CX) | Documentos de Microsoft
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: a24d5f45-8dbb-4540-958f-c76c90d8ed93
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f135907a4aba473db62734f9370ee82b7113c66d
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="template-ref-classes-ccx"></a>Clases ref de plantilla (C++/CX)
Las plantillas de C++ no se publican para metadatos y, por consiguiente, no pueden tener accesibilidad pública ni protegida en tu programa. Puedes, por supuesto, utilizar las plantillas de C++ estándar internamente en tu programa. Además, puedes definir una clase ref privada como plantilla y puedes declarar una clase ref de plantilla especializada de forma explícita como miembro privado de una clase ref pública.  
  
## <a name="authoring-ref-class-templates"></a>Crear plantillas de clase ref  
 En el ejemplo siguiente se muestra cómo declarar una clase ref privada como plantilla y también cómo declarar una plantilla de C++ estándar, y cómo declarar ambas como miembros de una clase ref pública. Tenga en cuenta que se puede especializar la plantilla estándar de C++ mediante un tipo en tiempo de ejecución de Windows, en este caso un Platform:: String ^.  
  
 [!code-cpp[cx_templates#01](../cppcx/codesnippet/CPP/templatedemo/class1.h#01)]  
  
## <a name="see-also"></a>Vea también  
 [Sistema de tipos (C++/CX)](../cppcx/type-system-c-cx.md)   
 [Referencia del lenguaje de Visual C++](../cppcx/visual-c-language-reference-c-cx.md)   
 [Referencia de espacios de nombres](../cppcx/namespaces-reference-c-cx.md)