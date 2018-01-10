---
title: "Administración de memoria: Bloques de memoria redimensionables | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fce06d27a091ad1740c882367358cf69a6dc3e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-resizable-memory-blocks"></a>Administración de memoria: Bloques de memoria redimensionables
El **nueva** y **eliminar** operadores, descritos en el artículo [administración de memoria: ejemplos](../mfc/memory-management-examples.md), son buenos para la asignación y desasignación de bloques de memoria de tamaño fijo y objetos. En ocasiones, la aplicación puede necesitar bloques de memoria redimensionables. Debe utilizar las funciones de biblioteca en tiempo de ejecución de C estándar [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md), y [libre](../c-runtime-library/reference/free.md) para administrar los bloques de memoria de tamaño variable en el montón.  
  
> [!IMPORTANT]
>  Mezclar la **nueva** y **eliminar** operadores con las funciones de asignación de memoria puede cambiar el tamaño en el mismo bloque de memoria dará como resultado una memoria dañada en la versión de depuración de MFC. No se debe usar `realloc` en un bloque de memoria asignada con **nueva**. Del mismo modo, no se debe asignar un bloque de memoria con el **nueva** operador y elimínelo con **libre**, o usar el **eliminar** operador en un bloque de memoria asignada con `malloc`.  
  
## <a name="see-also"></a>Vea también  
 [Administración de memoria: asignación del montón](../mfc/memory-management-heap-allocation.md)

