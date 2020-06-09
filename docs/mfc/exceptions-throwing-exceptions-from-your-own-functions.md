---
title: 'Excepciones: Iniciar excepciones desde sus propias funciones'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: ebdfea18e6e8445dd734bf43fb6a4ecf422975e9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622748"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Excepciones: Iniciar excepciones desde sus propias funciones

Es posible usar el paradigma de control de excepciones de MFC únicamente para detectar las excepciones producidas por las funciones de MFC o de otras bibliotecas. Además de detectar las excepciones producidas por el código de biblioteca, puede iniciar excepciones desde su propio código si está escribiendo funciones que pueden encontrar condiciones excepcionales.

Cuando se produce una excepción, se detiene la ejecución de la función actual y salta directamente al bloque **catch** del marco de excepción más interno. El mecanismo de excepción omite la ruta de acceso de salida normal de una función. Por lo tanto, debe asegurarse de eliminar los bloques de memoria que se eliminarán en una salida normal.

#### <a name="to-throw-an-exception"></a>Para producir una excepción

1. Use una de las funciones auxiliares de MFC, como `AfxThrowMemoryException` . Estas funciones inician un objeto de excepción preasignado del tipo adecuado.

   En el ejemplo siguiente, una función intenta asignar dos bloques de memoria y produce una excepción si se produce un error en alguna de las asignaciones:

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Si se produce un error en la primera asignación, simplemente puede producirse la excepción de memoria. Si la primera asignación es correcta pero se produce un error en la segunda, debe liberar el primer bloque de asignación antes de producir la excepción. Si ambas asignaciones se realizan correctamente, puede continuar normalmente y liberar los bloques al salir de la función.

     - O

1. Use una excepción definida por el usuario para indicar una condición de problema. Puede iniciar un elemento de cualquier tipo, incluso una clase completa, como excepción.

   En el ejemplo siguiente se intenta reproducir un sonido a través de un dispositivo de onda y se produce una excepción si se produce un error.

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> El control predeterminado de las excepciones de MFC solo se aplica a los punteros a `CException` objetos (y a objetos de `CException` clases derivadas de). En el ejemplo anterior se omite el mecanismo de excepciones de MFC.

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
