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
ms.openlocfilehash: e4fafd12d22f6ff7635380e139f60c110a193d9d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622821"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Excepciones: Liberar objetos en las excepciones

En este artículo se explica la necesidad y el método de liberar objetos cuando se produce una excepción. Contenido de los temas:

- [Controlar la excepción localmente](#_core_handling_the_exception_locally)

- [Producir excepciones después de destruir objetos](#_core_throwing_exceptions_after_destroying_objects)

Excepciones producidas por el marco de trabajo o por el flujo de programa normal de interrupción de la aplicación. Por lo tanto, es muy importante mantener un seguimiento estrecho de los objetos para que pueda desecharlos correctamente en caso de que se produzca una excepción.

Hay dos métodos principales para hacerlo.

- Controle las excepciones localmente mediante las palabras clave **try** y **catch** y destruya todos los objetos con una instrucción.

- Destruya cualquier objeto del bloque **catch** antes de producir la excepción fuera del bloque para un mayor control.

Estos dos enfoques se ilustran a continuación como soluciones para el siguiente ejemplo problemático:

[!code-cpp[NVC_MFCExceptions#14](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Tal como se ha escrito anteriormente, `myPerson` no se eliminará si se produce una excepción `SomeFunc` . La ejecución salta directamente al siguiente controlador de la excepción externa, omitiendo la salida de la función normal y el código que elimina el objeto. El puntero al objeto sale del ámbito cuando la excepción abandona la función y la memoria ocupada por el objeto nunca se recuperará mientras se esté ejecutando el programa. Se trata de una fuga de memoria; se detectaría mediante el diagnóstico de memoria.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Controlar la excepción localmente

El paradigma **try/catch** proporciona un método de programación defensivo para evitar pérdidas de memoria y asegurarse de que los objetos se destruyen cuando se producen excepciones. Por ejemplo, el ejemplo que se muestra anteriormente en este artículo podría volver a escribirse de la siguiente manera:

[!code-cpp[NVC_MFCExceptions#15](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Este nuevo ejemplo configura un controlador de excepciones para detectar la excepción y controlarla localmente. A continuación, sale de la función normalmente y destruye el objeto. El aspecto importante de este ejemplo es que un contexto para detectar la excepción se establece con los bloques **try/catch** . Sin un marco de excepción local, la función nunca sabría que se ha producido una excepción y no tendría la oportunidad de salir normalmente y destruir el objeto.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Producir excepciones después de destruir objetos

Otra manera de controlar las excepciones es pasarlos al siguiente contexto de control de excepciones externo. En el bloque **catch** , puede realizar una limpieza de los objetos asignados localmente y, a continuación, iniciar la excepción en para su posterior procesamiento.

La función de inicio puede necesitar o no la asignación de objetos de montón. Si la función siempre cancela la asignación del objeto de montón antes de que se devuelva en el caso normal, la función también debe desasignar el objeto de montón antes de producir la excepción. Por otro lado, si la función no suele desasignar el objeto antes de que se devuelva en el caso normal, debe decidir si se debe desasignar el objeto de montón.

En el ejemplo siguiente se muestra cómo se pueden limpiar los objetos asignados localmente:

[!code-cpp[NVC_MFCExceptions#16](codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

El mecanismo de excepción desasigna automáticamente los objetos Frame; también se llama al destructor del objeto de marco.

Si llama a funciones que pueden producir excepciones, puede usar bloques **try/catch** para asegurarse de que detecta las excepciones y tiene la oportunidad de destruir los objetos que ha creado. En concreto, tenga en cuenta que muchas funciones de MFC pueden producir excepciones.

Para obtener más información, vea [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)
