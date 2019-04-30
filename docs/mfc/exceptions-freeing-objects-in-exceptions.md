---
title: 'Excepciones: Liberar objetos en excepciones'
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
ms.openlocfilehash: 23fe85018d1bc2c41371afec2ad6931755e4e682
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406072"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Excepciones: Liberar objetos en excepciones

En este artículo se explica la necesidad y el método de liberación de objetos cuando se produce una excepción. Entre los temas se incluyen los siguientes:

- [Controlar la excepción localmente](#_core_handling_the_exception_locally)

- [Iniciar excepciones después de destruir objetos](#_core_throwing_exceptions_after_destroying_objects)

Excepciones iniciadas por el marco de trabajo o por el flujo normal del programa de interrupción de aplicación. Por lo tanto, es muy importante realizar un seguimiento cercano de objetos para que puede disponer de ellos en caso de que se produce una excepción.

Hay dos métodos principales para hacerlo.

- Controlar excepciones localmente mediante el **intente** y **catch** palabras clave, a continuación, destruya todos los objetos con una instrucción.

- Destruir cualquier objeto en el **catch** bloque antes de iniciar la excepción fuera del bloque para controlar aún más.

A continuación se ilustran estos dos enfoques como soluciones para el siguiente ejemplo de problema:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Como se escribió anteriormente, `myPerson` no se eliminarán si se produce una excepción por `SomeFunc`. La ejecución salta directamente al siguiente controlador de excepción externa, omitiendo la salida de función normal y el código que elimina el objeto. El puntero al objeto sale del ámbito cuando la excepción deja la función y la memoria ocupada por el objeto nunca se recuperarán siempre y cuando se ejecuta el programa. Se trata de una pérdida de memoria; se detectaría mediante el uso de los diagnósticos de memoria.

##  <a name="_core_handling_the_exception_locally"></a> Controlar la excepción localmente

El **try/catch** paradigma proporciona un método de programación defensivo para evitar pérdidas de memoria y asegurarse de que los objetos se destruyen cuando se producen excepciones. Por ejemplo, el ejemplo mostrado anteriormente en este artículo se podría reescribir del siguiente modo:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Este nuevo ejemplo configura un controlador de excepciones para detectar la excepción y controlarla localmente. A continuación, sale de la función con normalidad y destruye el objeto. El aspecto importante de este ejemplo es que se ha establecido un contexto para detectar la excepción con el **try/catch** bloques. Sin un marco de excepción local, la función nunca sabrá que una excepción se ha iniciado y no tendría la oportunidad de salir normalmente y destruir el objeto.

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> Iniciar excepciones después de destruir objetos

Otra manera de controlar las excepciones es pasarlas el contexto de control de excepciones externo siguiente. En su **catch** bloque, puede hacer una limpieza de los objetos asignados localmente y, a continuación, inicia la excepción para su posterior procesamiento.

La función iniciadora puede o no es posible que deba desasignar objetos del montón. Si la función siempre desasigna el objeto de montón antes de devolver en el caso normal, la función también debe desasignar el objeto de montón de antes de iniciar la excepción. Por otro lado, si la función suele desasignar el objeto antes de devolver en el caso normal, a continuación, debe decidir caso por caso si el objeto de montón debe desasignarse.

El ejemplo siguiente se muestra cómo localmente los objetos asignados se puede limpiar:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

El mecanismo de excepción desasigna automáticamente los objetos de marco; También se llama al destructor del objeto frame.

Si se llama a funciones que pueden producir excepciones, puede usar **try/catch** bloques para asegurarse de que detecte las excepciones y que tiene una oportunidad para destruir los objetos que ha creado. En concreto, tenga en cuenta que muchas funciones MFC pueden producir excepciones.

Para obtener más información, consulte [excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)
