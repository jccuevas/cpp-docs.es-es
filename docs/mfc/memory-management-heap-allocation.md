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
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626292"
---
# <a name="memory-management-heap-allocation"></a>Administración de memoria: Asignación del montón

El montón se reserva para las necesidades de asignación de memoria del programa. Es un área aparte del código de programa y la pila. Los programas típicos de C usan las funciones **malloc** y **Free** para asignar y desasignar memoria de montón. La versión de depuración de MFC proporciona versiones modificadas de los operadores integrados de C++ **New** y **Delete** para asignar y desasignar objetos en la memoria del montón.

Cuando se usa **New** y **Delete** en lugar de **malloc** y **Free**, se pueden aprovechar las mejoras en la depuración de la administración de memoria de la biblioteca de clases, lo que puede resultar útil para detectar pérdidas de memoria. Al compilar el programa con la versión de lanzamiento de MFC, las versiones estándar de los operadores **New** y **Delete** proporcionan una manera eficaz de asignar y desasignar memoria (la versión de lanzamiento de MFC no proporciona versiones modificadas de estos operadores).

Tenga en cuenta que el tamaño total de los objetos asignados en el montón solo está limitado por la memoria virtual disponible del sistema.

## <a name="see-also"></a>Consulte también

[Administración de memoria](memory-management.md)
