---
title: 'Excepciones: Iniciar excepciones desde sus propias funciones | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a26bd11c2a37e3644333a95ed03d9182f7b32b87
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066115"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>Excepciones: Iniciar excepciones desde sus propias funciones

Es posible usar el paradigma de control de excepciones de MFC solamente para detectar las excepciones producidas por las funciones de MFC u otras bibliotecas. Además de detectar las excepciones producidas por código de biblioteca, puede iniciar excepciones desde su propio código si va a escribir las funciones que pueden encontrar situaciones excepcionales.

Cuando se produce una excepción, la ejecución de la función actual se detiene y salta directamente a la **catch** bloque del marco de la excepción interna. El mecanismo de excepciones omite la ruta de acceso de salida normal de una función. Por lo tanto, debe asegurarse de eliminar los bloques de memoria que se eliminarán en una salida normal.

#### <a name="to-throw-an-exception"></a>Para producir una excepción

1. Use una de las funciones auxiliares MFC, como `AfxThrowMemoryException`. Estas funciones producen un objeto de excepción preasignado del tipo adecuado.

   En el ejemplo siguiente, una función intenta asignar dos bloques de memoria y produce una excepción si se produce un error en cualquier asignación:

   [!code-cpp[NVC_MFCExceptions#17](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   Si se produce un error en la primera asignación, se puede producir la excepción de memoria. Si la primera asignación es correcta, pero se produce un error en la otra, debe liberar el primer bloque de asignación antes de iniciar la excepción. Si ambas asignaciones se realizan correctamente, puede continuar normalmente y liberar los bloques al salir de la función.

     - O

1. Utilice una excepción definida por el usuario para indicar una condición de problema. Puede iniciar un elemento de cualquier tipo, incluso una clase entera, como la excepción.

   El ejemplo siguiente se intenta reproducir un sonido a través de un dispositivo de onda y produce una excepción si se produce un error.

   [!code-cpp[NVC_MFCExceptions#18](../mfc/codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
>  De MFC control predeterminado de las excepciones solo se aplica a punteros a `CException` objetos (y los objetos de `CException`-las clases derivadas). El ejemplo anterior omite el mecanismo de excepciones de MFC.

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)

