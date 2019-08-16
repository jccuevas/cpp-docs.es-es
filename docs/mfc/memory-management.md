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
ms.openlocfilehash: 5d81bd0a8bdd24059951cba5c8b69751b3d1db86
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508272"
---
# <a name="memory-management"></a>Administración de memoria

En este grupo de artículos se describe cómo sacar partido de los servicios de uso general del biblioteca MFC (MFC) relacionados con la administración de memoria. La asignación de memoria puede dividirse en dos categorías principales: asignaciones de Marcos y asignaciones de montón.

Una diferencia principal entre las dos técnicas de asignación es que con la asignación de fotogramas suele trabajar con el propio bloque de memoria real, mientras que con la asignación del montón siempre se proporciona un puntero al bloque de memoria. Otra diferencia importante entre los dos esquemas es que los objetos Frame se eliminan automáticamente, mientras que los objetos heap deben ser eliminados explícitamente por el programador.

Para obtener información sobre la administración de memoria en los programas para Windows, vea [Administración de memoria](/windows/win32/memory/memory-management) en el Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Asignación de marcos](../mfc/memory-management-frame-allocation.md)

- [Asignación del montón](../mfc/memory-management-heap-allocation.md)

- [Asignar memoria para una matriz](../mfc/memory-management-examples.md)

- [Desasignar memoria para una matriz del montón](../mfc/memory-management-examples.md)

- [Asignar memoria para una estructura de datos](../mfc/memory-management-examples.md)

- [Asignar memoria para un objeto](../mfc/memory-management-examples.md)

- [Bloques de memoria de tamaño variable](../mfc/memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)
