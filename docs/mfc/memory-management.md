---
title: Administración de memoria
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: b5b91245d08c6c4a17c9ba96a0ca4dcf19932d9f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50461387"
---
# <a name="memory-management"></a>Administración de memoria

Este grupo de artículos describe cómo aprovechar las ventajas de los servicios de uso general de la base clase biblioteca MFC (Microsoft) relacionados con la administración de memoria. Asignación de memoria puede dividirse en dos categorías principales: las asignaciones y las asignaciones del montón de fotogramas.

Una diferencia principal entre las dos técnicas de asignación es que con la asignación de marcos, que normalmente trabajará con la memoria real propio bloque, mientras que con la asignación del montón siempre se proporciona un puntero al bloque de memoria. Otra diferencia importante entre los dos esquemas es que automáticamente se eliminan objetos de fotogramas, mientras que los objetos del montón se deben eliminar explícitamente por el programador.

Para obtener información sobre la administración de memoria en programas de Windows no basados en MFC, vea [administración de memoria](https://msdn.microsoft.com/library/windows/desktop/aa366779) en el SDK de Windows.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Asignación de marcos](../mfc/memory-management-frame-allocation.md)

- [Asignación del montón](../mfc/memory-management-heap-allocation.md)

- [Asignación de memoria para una matriz](../mfc/memory-management-examples.md)

- [Desasignar memoria para una matriz desde el montón](../mfc/memory-management-examples.md)

- [Asignación de memoria para una estructura de datos](../mfc/memory-management-examples.md)

- [Asignación de memoria para un objeto](../mfc/memory-management-examples.md)

- [Bloques de memoria redimensionables](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)

