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
ms.openlocfilehash: 464a31491f2c3017453bdd5bbdc8b059d348eb3c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626258"
---
# <a name="memory-management"></a>Administración de memoria

En este grupo de artículos se describe cómo sacar partido de los servicios de uso general del biblioteca MFC (MFC) relacionados con la administración de memoria. La asignación de memoria puede dividirse en dos categorías principales: asignaciones de Marcos y asignaciones de montón.

Una diferencia principal entre las dos técnicas de asignación es que con la asignación de fotogramas suele trabajar con el propio bloque de memoria real, mientras que con la asignación del montón siempre se proporciona un puntero al bloque de memoria. Otra diferencia importante entre los dos esquemas es que los objetos Frame se eliminan automáticamente, mientras que los objetos heap deben ser eliminados explícitamente por el programador.

Para obtener información sobre la administración de memoria en los programas para Windows, vea [Administración de memoria](/windows/win32/memory/memory-management) en el Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Asignación de marcos](memory-management-frame-allocation.md)

- [Asignación del montón](memory-management-heap-allocation.md)

- [Asignar memoria para una matriz](memory-management-examples.md)

- [Desasignar memoria para una matriz del montón](memory-management-examples.md)

- [Asignar memoria para una estructura de datos](memory-management-examples.md)

- [Asignar memoria para un objeto](memory-management-examples.md)

- [Bloques de memoria de tamaño variable](memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Consulte también

[Conceptos](mfc-concepts.md)<br/>
[Temas generales de MFC](general-mfc-topics.md)
