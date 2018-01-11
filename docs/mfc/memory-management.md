---
title: "Administración de memoria | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9e31fc1136249f843aa5dc96a4caffcccc7a85
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management"></a>Administración de memoria
Este grupo de artículos describe cómo aprovechar las ventajas de los servicios de uso generales de la biblioteca de clase de Foundation de Microsoft (MFC) relacionados con la administración de memoria. Asignación de memoria puede dividirse en dos categorías principales: las asignaciones y las asignaciones de montones de marco.  
  
 Una diferencia principal entre las dos técnicas de asignación es que con la asignación de marcos que normalmente trabajará con la memoria real propio bloque, mientras que con la asignación en el montón siempre se recibe un puntero al bloque de memoria. Otra diferencia importante entre los dos esquemas es que los objetos de marco se eliminan automáticamente, mientras los objetos del montón se deben eliminar explícitamente por el programador.  
  
 Para obtener información sobre la administración de memoria en programas de Windows no están basados en MFC, vea [administración de memoria](http://msdn.microsoft.com/library/windows/desktop/aa366779) del SDK de Windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Asignación de marcos](../mfc/memory-management-frame-allocation.md)  
  
-   [Asignación en el montón](../mfc/memory-management-heap-allocation.md)  
  
-   [Asignación de memoria para una matriz](../mfc/memory-management-examples.md)  
  
-   [Desasignación de memoria para una matriz desde el montón](../mfc/memory-management-examples.md)  
  
-   [Asignar memoria para una estructura de datos](../mfc/memory-management-examples.md)  
  
-   [Asignación de memoria de un objeto](../mfc/memory-management-examples.md)  
  
-   [Bloques de memoria redimensionables](../mfc/memory-management-resizable-memory-blocks.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)

