---
title: 'Administración de memoria: Bloques de memoria redimensionables'
ms.date: 11/04/2016
helpviewer_keywords:
- memory blocks [MFC], resizable
- memory [MFC], corruption
- memory allocation [MFC], memory block size
- memory blocks [MFC], allocating
- blocks [MFC], memory allocation
- resizable memory blocks [MFC]
ms.assetid: f0efe6f4-a3ed-4541-9195-51ec1291967a
ms.openlocfilehash: b048b60a5512ecc54750cb980ca67e2373e2c837
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364775"
---
# <a name="memory-management-resizable-memory-blocks"></a>Administración de memoria: Bloques de memoria redimensionables

Los operadores **new** y **delete,** descritos en el artículo [Memory Management: Examples](../mfc/memory-management-examples.md), son buenos para asignar y desasignar bloques y objetos de memoria de tamaño fijo. En ocasiones, es posible que la aplicación necesite bloques de memoria redimensionables. Debe utilizar las funciones estándar de biblioteca en tiempo de ejecución de C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)y [free](../c-runtime-library/reference/free.md) para administrar bloques de memoria redimensionables en el montón.

> [!IMPORTANT]
> La mezcla de los operadores **new** y **delete** con las funciones de asignación de memoria redimensionables en el mismo bloque de memoria dará como resultado memoria dañada en la versión de depuración de MFC. No debe utilizar **realloc** en un bloque de memoria asignado con **new**. Del mismo modo, no debe asignar un bloque de memoria con el **operador new** y eliminarlo con **free**, o utilizar el operador **delete** en un bloque de memoria asignado con **malloc**.

## <a name="see-also"></a>Consulte también

[Administración de memoria: Asignación del montón](../mfc/memory-management-heap-allocation.md)
