---
title: "Administraci&#243;n de memoria: Bloques de memoria redimensionables | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "bloques, asignación de memoria"
  - "asignación de memoria, tamaño del bloque de memoria"
  - "bloques de memoria, asignar"
  - "bloques de memoria, tamaño ajustable"
  - "memoria, daños"
  - "bloques de memoria de tamaño ajustable"
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Administraci&#243;n de memoria: Bloques de memoria redimensionables
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los operadores de **new** y de **borrar** , descritos en el caso [Administración de memoria: Ejemplos](../mfc/memory-management-examples.md), son buenos para asignar y desasignar los bloques y los objetos de memoria de tamaño fijo.  En ocasiones, la aplicación puede necesitar los bloques de memoria de tamaño variable.  Debe utilizar las funciones de la biblioteca en tiempo de ejecución estándar de C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), y [libre](../c-runtime-library/reference/free.md) para administrar los bloques de memoria existe en la pila.  
  
> [!IMPORTANT]
>  Mezclar los operadores de **new** y de **borrar** con las funciones de asignación de memoria de tamaño variable en el mismo bloque de memoria dará lugar a memoria dañado en la versión de depuración de MFC.  No debe utilizar `realloc` en un bloque de memoria asignado con **new**.  Igualmente, no debe asignar un bloque de memoria con el operador de **new** y eliminarlo con **free**, o utilice el operador de **borrar** en un bloque de memoria asignado con `malloc`.  
  
## Vea también  
 [Administración de memoria: Asignación del montón](../mfc/memory-management-heap-allocation.md)