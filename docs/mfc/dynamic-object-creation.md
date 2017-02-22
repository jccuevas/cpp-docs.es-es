---
title: "Creaci&#243;n de objetos din&#225;micos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CObject (clase), creación de objetos dinámicos"
  - "creación de objetos dinámicos"
  - "creación de objetos, dinámicamente en tiempo de ejecución"
  - "objetos [C++], crear dinámicamente en tiempo de ejecución"
ms.assetid: 3e0f51cb-3e24-4231-817f-1c0ce9f2d5df
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Creaci&#243;n de objetos din&#225;micos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo crear un objeto dinámicamente en tiempo de ejecución.  El procedimiento utiliza la información de la clase en tiempo de ejecución, como se describe en el artículo [Información de acceso de la clase en tiempo de ejecución](../mfc/accessing-run-time-class-information.md).  
  
#### Para crear dinámicamente un objeto dado su clase en tiempo de ejecución  
  
1.  Utilice el código siguiente para crear dinámicamente un objeto mediante la función de `CreateObject` de `CRuntimeClass`.  Observe que en el error, `CreateObject` devuelve **nulo** en lugar de provocar una excepción:  
  
     [!code-cpp[NVC_MFCCObjectSample#6](../mfc/codesnippet/CPP/dynamic-object-creation_1.cpp)]  
  
## Vea también  
 [Usar CObject](../mfc/using-cobject.md)