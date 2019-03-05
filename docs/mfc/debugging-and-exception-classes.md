---
title: Clases de excepciones y depuración
ms.date: 11/04/2016
f1_keywords:
- vc.classes.debug
helpviewer_keywords:
- debugging [MFC], exception classes
- debugging [MFC], classes for debugging
ms.assetid: 0d158efd-2e62-452e-9d2a-d3c30dfee7f9
ms.openlocfilehash: 328d7a38c544b56f83ea3e8b1136b1122c4dfa14
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271416"
---
# <a name="debugging-and-exception-classes"></a>Clases de excepciones y depuración

Estas clases proporcionan compatibilidad para la depuración de asignación de memoria dinámica y para pasar información de excepción de la función donde se produjo la excepción a la función donde se detecta.

Utilizar clases [CDumpContext](../mfc/reference/cdumpcontext-class.md) y [CMemoryState](../mfc/reference/cmemorystate-structure.md) durante el desarrollo para ayudar con la depuración, como se describe en [depurar aplicaciones de MFC](/visualstudio/debugger/mfc-debugging-techniques). Use [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md) para determinar la clase de cualquier objeto en tiempo de ejecución, como se describe en el artículo [acceso a información de clase de tiempo de ejecución](../mfc/accessing-run-time-class-information.md). El marco usa `CRuntimeClass` para crear objetos de una clase determinada de forma dinámica.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
