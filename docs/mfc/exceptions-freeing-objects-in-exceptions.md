---
title: 'Excepciones: Liberar objetos en las excepciones'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371999"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Excepciones: Liberar objetos en las excepciones

En este artículo se explica la necesidad y el método de liberación de objetos cuando se produce una excepción. Contenido de los temas:

- [Manejo de la excepción localmente](#_core_handling_the_exception_locally)

- [Lanzar excepciones después de destruir objetos](#_core_throwing_exceptions_after_destroying_objects)

Las excepciones producidas por el marco de trabajo o por la aplicación interrumpen el flujo normal del programa. Por lo tanto, es muy importante mantener un seguimiento cercano de los objetos para que pueda eliminarlos correctamente en caso de que se produzca una excepción.

Hay dos métodos principales para hacer esto.

- Controle las excepciones localmente mediante las palabras clave **try** y **catch** y, a continuación, destruya todos los objetos con una instrucción.

- Destruye cualquier objeto del bloque **catch** antes de producir la excepción fuera del bloque para su posterior control.

Estos dos enfoques se ilustran a continuación como soluciones para el siguiente ejemplo problemático:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Como se `myPerson` ha escrito anteriormente, no se `SomeFunc`eliminará si se produce una excepción por . La ejecución salta directamente al siguiente controlador de excepciones externo, omitiendo la salida de función normal y el código que elimina el objeto. El puntero al objeto sale del ámbito cuando la excepción sale de la función y la memoria ocupada por el objeto nunca se recuperará mientras se ejecute el programa. Esto es una pérdida de memoria; se detectaría mediante el diagnóstico de memoria.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Manejo de la excepción localmente

El paradigma **try/catch** proporciona un método de programación defensivo para evitar pérdidas de memoria y garantizar que los objetos se destruyen cuando se producen excepciones. Por ejemplo, el ejemplo mostrado anteriormente en este artículo podría reescribirse de la siguiente manera:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

En este nuevo ejemplo se configura un controlador de excepciones para detectar la excepción y controlarla localmente. A continuación, sale de la función normalmente y destruye el objeto. El aspecto importante de este ejemplo es que se establece un contexto para detectar la excepción con los bloques **try/catch.** Sin un marco de excepción local, la función nunca sabría que se ha producido una excepción y no tendría la oportunidad de salir normalmente y destruir el objeto.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Lanzar excepciones después de destruir objetos

Otra forma de controlar las excepciones es pasarlas al siguiente contexto de control de excepciones externo. En el bloque **catch,** puede realizar una limpieza de los objetos asignados localmente y, a continuación, iniciar la excepción para su posterior procesamiento.

La función de lanzamiento puede o no es necesario desasignar objetos de montón. Si la función siempre desasigna el objeto de montón antes de devolver en el caso normal, la función también debe desasignar el objeto de montón antes de producir la excepción. Por otro lado, si la función normalmente no desasigna el objeto antes de devolverlo en el caso normal, debe decidir caso por caso si se debe desasignar el objeto de montón.

En el ejemplo siguiente se muestra cómo se pueden limpiar los objetos asignados localmente:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

El mecanismo de excepción desasigna automáticamente los objetos de marco; también se llama al destructor del objeto frame.

Si llama a funciones que pueden producir excepciones, puede usar bloques **try/catch** para asegurarse de que detecta las excepciones y tiene la oportunidad de destruir los objetos que ha creado. En particular, tenga en cuenta que muchas funciones MFC pueden producir excepciones.

Para obtener más información, vea [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
