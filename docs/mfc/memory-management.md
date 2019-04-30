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
ms.openlocfilehash: 1c7f901009d5e1e7f0af20d493bb748b46b18480
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219136"
---
# <a name="memory-management"></a>Administración de memoria

Este grupo de artículos describe cómo aprovechar las ventajas de los servicios de uso general de la base clase biblioteca MFC (Microsoft) relacionados con la administración de memoria. Asignación de memoria puede dividirse en dos categorías principales: las asignaciones y las asignaciones del montón de fotogramas.

Una diferencia principal entre las dos técnicas de asignación es que con la asignación de marcos, que normalmente trabajará con la memoria real propio bloque, mientras que con la asignación del montón siempre se proporciona un puntero al bloque de memoria. Otra diferencia importante entre los dos esquemas es que automáticamente se eliminan objetos de fotogramas, mientras que los objetos del montón se deben eliminar explícitamente por el programador.

Para obtener información sobre la administración de memoria en programas de Windows no basados en MFC, vea [administración de memoria](/windows/desktop/memory/memory-management) en el SDK de Windows.

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
