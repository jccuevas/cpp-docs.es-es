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
ms.openlocfilehash: 74ae94146b1ec711b586ea1fecbbc89a47b40b5e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626279"
---
# <a name="memory-management-resizable-memory-blocks"></a>Administración de memoria: Bloques de memoria redimensionables

Los operadores **New** y **Delete** , que se describen en el artículo [Administración de memoria: ejemplos](memory-management-examples.md), son buenos para asignar y desasignar objetos y bloques de memoria de tamaño fijo. En ocasiones, es posible que la aplicación necesite bloques de memoria de tamaño variable. Debe usar las funciones de biblioteca en tiempo de ejecución estándar de C [malloc](../c-runtime-library/reference/malloc.md), [realloc](../c-runtime-library/reference/realloc.md)y [Free](../c-runtime-library/reference/free.md) para administrar bloques de memoria redimensionables en el montón.

> [!IMPORTANT]
> La combinación de los operadores **New** y **Delete** con las funciones de asignación de memoria de tamaño variable en el mismo bloque de memoria producirá una memoria dañada en la versión de depuración de MFC. No debe usar **realloc** en un bloque de memoria asignado a **New**. Del mismo modo, no debe asignar un bloque de memoria con el operador **New** y eliminarlo de forma **gratuita**, ni utilizar el operador **Delete** en un bloque de memoria asignado a **malloc**.

## <a name="see-also"></a>Consulte también

[Administración de memoria: Asignación del montón](memory-management-heap-allocation.md)
