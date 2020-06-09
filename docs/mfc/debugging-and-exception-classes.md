---
title: Clases de excepciones y depuración
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 6c7d1fc20556993c3c6690122786d7a767d895ad
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625937"
---
# <a name="debugging-and-exception-classes"></a>Clases de excepciones y depuración

Estas clases proporcionan compatibilidad para la depuración de la asignación de memoria dinámica y para pasar información de excepción de la función en la que se produce la excepción a la función en la que se detecta.

Use las clases [CDumpContext](reference/cdumpcontext-class.md) y [CMemoryState](reference/cmemorystate-structure.md) durante el desarrollo para ayudar con la depuración, como se describe en [depuración de aplicaciones MFC](/visualstudio/debugger/mfc-debugging-techniques). Use [CRuntimeClass](reference/cruntimeclass-structure.md) para determinar la clase de cualquier objeto en tiempo de ejecución, como se describe en el artículo [acceso a la información de clase en tiempo de ejecución](accessing-run-time-class-information.md). El marco de trabajo usa `CRuntimeClass` para crear dinámicamente los objetos de una clase determinada.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
