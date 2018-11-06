---
title: 'Administración de memoria: Asignación del montón'
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
ms.openlocfilehash: 0c669fa611193b9a04e4854c84dec604e585991c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641160"
---
# <a name="memory-management-heap-allocation"></a>Administración de memoria: Asignación del montón

El montón está reservado para las necesidades de la asignación de memoria del programa. Es un área independiente del código del programa y la pila. Típicos programas de C usa las funciones **malloc** y **libre** para asignar y desasignar memoria del montón. La versión de depuración de MFC proporciona versiones modificadas de los operadores integrados de C++ **nueva** y **eliminar** para asignar y desasignar objetos en memoria en montón.

Cuando usas **nueva** y **eliminar** en lugar de **malloc** y **libre**, podrá aprovechar las ventajas de la biblioteca de clases administración de memoria las mejoras de depuración, que pueden ser útiles para detectar pérdidas de memoria. Al compilar el programa con la versión de lanzamiento de MFC, las versiones estándar de la **nueva** y **eliminar** operadores proporcionan un modo eficaz para asignar y desasignar memoria (la versión de lanzamiento de MFC no proporciona versiones modificadas de estos operadores).

Tenga en cuenta que el tamaño total de objetos asignados en el montón está limitado únicamente por la memoria virtual disponible de su sistema.

## <a name="see-also"></a>Vea también

[Administración de memoria](../mfc/memory-management.md)

