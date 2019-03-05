---
title: 'Excepciones: Excepciones en los constructores'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271019"
---
# <a name="exceptions-exceptions-in-constructors"></a>Excepciones: Excepciones en los constructores

Cuando se lanza una excepción en un constructor, limpiar los objetos y las asignaciones de memoria realizadas antes de iniciar la excepción, como se explica en [excepciones: Iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Cuando se lanza una excepción en un constructor, la memoria para el propio objeto ya se ha asignado en el momento en que se llama al constructor. Por lo tanto, el compilador desasignará automáticamente la memoria ocupada por el objeto después de que se produce la excepción.

Para obtener más información, consulte [excepciones: Liberar objetos en excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
