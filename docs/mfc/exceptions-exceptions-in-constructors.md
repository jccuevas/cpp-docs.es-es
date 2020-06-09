---
title: 'Excepciones: Excepciones en los constructores'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 4089f4d44f03c7de3432f137b5d28f74189e1cb9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624611"
---
# <a name="exceptions-exceptions-in-constructors"></a>Excepciones: Excepciones en los constructores

Al iniciar una excepción en un constructor, limpie cualquier objeto y las asignaciones de memoria que haya realizado antes de producir la excepción, como se explica en [excepciones: iniciar excepciones desde sus propias funciones](exceptions-throwing-exceptions-from-your-own-functions.md).

Al iniciar una excepción en un constructor, ya se ha asignado la memoria para el propio objeto en el momento en que se llama al constructor. Por lo tanto, el compilador desasignará automáticamente la memoria ocupada por el objeto después de que se produzca la excepción.

Para obtener más información, vea [excepciones: liberar objetos en excepciones](exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
