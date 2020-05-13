---
title: 'Excepciones: Iniciar excepciones desde sus propias funciones'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 6484594df7636fd52ac46ab1cc212c8e2ec0278e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359274"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Excepciones: Iniciar excepciones desde sus propias funciones

Es posible usar el paradigma de control de excepciones MFC únicamente para detectar excepciones producidas por funciones en MFC u otras bibliotecas. Además de detectar excepciones producidas por el código de biblioteca, puede producir excepciones desde su propio código si está escribiendo funciones que pueden encontrar condiciones excepcionales.

Cuando se produce una excepción, se detiene la ejecución de la función actual y salta directamente al bloque **catch** del marco de excepción más interno. El mecanismo de excepción omite la ruta de acceso de salida normal de una función. Por lo tanto, debe asegurarse de eliminar los bloques de memoria que se eliminarían en una salida normal.

#### <a name="to-throw-an-exception"></a>Para lanzar una excepción

1. Utilice una de las funciones `AfxThrowMemoryException`auxiliares de MFC, como . Estas funciones producen un objeto de excepción preasignado del tipo adecuado.

   En el ejemplo siguiente, una función intenta asignar dos bloques de memoria y produce una excepción si se produce un error en cualquiera de las asignaciones:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Si se produce un error en la primera asignación, simplemente puede iniciar la excepción de memoria. Si la primera asignación se realiza correctamente pero se produce un error en la segunda, debe liberar el primer bloque de asignación antes de iniciar la excepción. Si ambas asignaciones se realizan correctamente, puede proceder normalmente y liberar los bloques al salir de la función.

     - O bien

1. Utilice una excepción definida por el usuario para indicar una condición de problema. Puede producir un elemento de cualquier tipo, incluso una clase completa, como excepción.

   En el ejemplo siguiente se intenta reproducir un sonido a través de un dispositivo de onda y se produce una excepción si se produce un error.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> El control predeterminado de excepciones de MFC `CException` solo se `CException`aplica a los punteros a objetos (y objetos de clases derivadas). En el ejemplo anterior se omite el mecanismo de excepción de MFC.

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
