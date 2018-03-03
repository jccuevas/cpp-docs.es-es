---
title: 'Excepciones: Liberar objetos en excepciones | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a422347e319fabbd91f20e0ebf7897865f1ca4c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Excepciones: Liberar objetos en las excepciones
Este artículo explica la necesidad y el método de liberar objetos cuando se produce una excepción. Entre los temas se incluyen los siguientes:  
  
-   [Controlar la excepción localmente](#_core_handling_the_exception_locally)  
  
-   [Producir excepciones después de destruir objetos](#_core_throwing_exceptions_after_destroying_objects)  
  
 Excepciones producidas por el marco de trabajo o por el flujo normal del programa de interrupción de aplicación. Por lo tanto, es muy importante realizar un seguimiento cercano de objetos para que puede disponer de ellos en caso de que se produce una excepción.  
  
 Hay dos métodos principales para hacerlo.  
  
-   Controlar excepciones localmente mediante el **intente** y **catch** palabras clave, a continuación, destruye todos los objetos con una instrucción.  
  
-   Destruir cualquier objeto en el **catch** bloque antes de iniciar la excepción fuera del bloque para controlar aún más.  
  
 Estos dos enfoques se muestran a continuación como soluciones a las problemas del ejemplo siguiente:  
  
 [!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]  
  
 Como se indica anteriormente, `myPerson` no se eliminará si se produce una excepción por `SomeFunc`. Ejecución salta directamente al siguiente controlador de excepción exterior, omitiendo la salida de función normal y el código que elimina el objeto. El puntero al objeto se sale del ámbito cuando la excepción deja la función y la memoria ocupada por el objeto nunca se recuperarán siempre y cuando se ejecuta el programa. Se trata de una pérdida de memoria; se detectaría mediante el uso de los diagnósticos de memoria.  
  
##  <a name="_core_handling_the_exception_locally"></a>Controlar la excepción localmente  
 El **try/catch** paradigma proporciona un método de programación estable para evitar pérdidas de memoria y garantizar que los objetos se destruyen cuando se producen excepciones. Por ejemplo, el ejemplo mostrado anteriormente en este artículo puede reescribirse como sigue:  
  
 [!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]  
  
 Este nuevo ejemplo configura un controlador de excepciones para detectar la excepción y controlarla localmente. A continuación, sale de la función normalmente y destruye el objeto. El aspecto importante de este ejemplo es que se ha establecido un contexto para detectar la excepción con la **try/catch** bloques. Sin un marco de excepción local, la función nunca sabría que una excepción se ha iniciado y no tendrán la oportunidad de salir normalmente y destruir el objeto.  
  
##  <a name="_core_throwing_exceptions_after_destroying_objects"></a>Producir excepciones después de destruir objetos  
 Otra manera de controlar las excepciones es pasarlas el contexto de control de excepciones externo siguiente. En su **catch** bloque, puede hacer una limpieza de los objetos asignados localmente y, a continuación, inicia la excepción para su posterior procesamiento.  
  
 La función iniciadora puede o no necesitar desasignar objetos del montón. Si la función siempre desasigna el objeto del montón antes de devolver en el caso normal, la función también debe desasignar el objeto de montón de antes de iniciar la excepción. Por otro lado, si la función no suele desasignar el objeto antes de devolver en el caso normal, a continuación, debe decidir caso por caso si debe desasignarse el objeto de montón.  
  
 El ejemplo siguiente se muestra cómo localmente los objetos asignados se puede limpiar:  
  
 [!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]  
  
 El mecanismo de excepción desasigna automáticamente los objetos de marco; También se llama al destructor del objeto de marco.  
  
 Si se llama a funciones que pueden producir excepciones, puede usar **try/catch** bloques para asegurarse de que detectar las excepciones y tiene una oportunidad para destruir los objetos que ha creado. En concreto, tenga en cuenta que muchas funciones MFC pueden producir excepciones.  
  
 Para obtener más información, consulte [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

