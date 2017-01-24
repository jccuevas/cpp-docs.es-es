---
title: "_CRTDBG_MAP_ALLOC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CRTDBG_MAP_ALLOC"
  - "_CRTDBG_MAP_ALLOC"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRTDBG_MAP_ALLOC (macro)"
  - "asignación de memoria, en compilaciones de depuración"
  - "CRTDBG_MAP_ALLOC (macro)"
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CRTDBG_MAP_ALLOC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando el marcador de **\_CRTDBG\_MAP\_ALLOC** se define en la versión de depuración de una aplicación, la versión base de las funciones del montón se asigna directamente a sus versiones de depuración.  El marcador se utiliza en Crtdbg.h para realizar la asignación.  Este marcador está disponible únicamente cuando el indicador de [\_DEBUG](../c-runtime-library/debug.md) definida en la aplicación.  
  
 Para obtener más información sobre cómo utilizar la versión de depuración con la versión base de una función de la pila, vea [Con la versión Versus de depuración la versión base](../Topic/Debug%20Versions%20of%20Heap%20Allocation%20Functions.md).  
  
## Vea también  
 [Marcas de control](../c-runtime-library/control-flags.md)