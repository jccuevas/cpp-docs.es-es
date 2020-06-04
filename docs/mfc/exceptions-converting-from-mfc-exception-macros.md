---
title: 'Excepciones: Convertir desde macros de excepciones de MFC'
ms.date: 08/27/2018
helpviewer_keywords:
- converting exceptions [MFC]
- exception objects [MFC]
- conversions [MFC], code written with MFC macros
- keywords [MFC], macros
- macrosv, C++ keywords
- exception objects [MFC], deleting
- CException class [MFC], deleting CException class objects
- exceptions [MFC], converting
- exceptions [MFC], deleting exception objects
- catch blocks [MFC], delimiting
- exception handling [MFC], converting exceptions
ms.assetid: bd3ac3b3-f3ce-4fdd-a168-a2cff13ed796
ms.openlocfilehash: 330f66b1f46542082637645ad53da016b434d4a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372016"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Excepciones: Convertir desde macros de excepciones de MFC

Este es un tema avanzado.

En este artículo se explica cómo convertir código existente escrito con macros de Microsoft Foundation Class **(TRY**, **CATCH**, **THROW**, etc.) para usar las palabras clave de control de excepciones de C++ **try,** **catch**y **throw**. Contenido de los temas:

- [Ventajas de conversión](#_core_advantages_of_converting)

- [Conversión de código con macros de excepción para usar excepciones C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Ventajas de la conversión

Probablemente no es necesario convertir el código existente, aunque debe tener en cuenta las diferencias entre las implementaciones de macro en MFC versión 3.0 y las implementaciones en versiones anteriores. Estas diferencias y los cambios posteriores en el comportamiento del código se describen en [Excepciones: cambios en](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)macros de excepciones en la versión 3.0 .

Las principales ventajas de la conversión son:

- El código que usa las palabras clave de control de excepciones de C++ se compila en un archivo . EXE o . Dll.

- Las palabras clave de control de excepciones de C++ son más versátiles: pueden controlar las excepciones de cualquier tipo de datos que `CException` se pueda nitar **(int**, **float**, **char,** etc.), mientras que las macros solo controlan las excepciones de clase y clases derivadas de ella.

La principal diferencia entre las macros y las palabras clave es que el código que usa las macros "automáticamente" elimina una excepción detectada cuando la excepción sale del ámbito. El código que usa las palabras clave no lo hace, por lo que debe eliminar explícitamente una excepción detectada. Para obtener más información, consulte el artículo [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

Otra diferencia es la sintaxis. La sintaxis de macros y palabras clave difiere en tres aspectos:

1. Argumentos macro y declaraciones de excepción:

   Una invocación de macro **CATCH** tiene la sintaxis siguiente:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Observe la coma entre el nombre de clase y el nombre del puntero de objeto.

   La declaración de excepción para la palabra clave **catch** utiliza esta sintaxis:

   **catch(** *exception_type* *exception_name* **)**

   Esta instrucción de declaración de excepción indica el tipo de excepción que controla el bloque catch.

2. Delimitación de bloques de captura:

   Con las macros, la macro **CATCH** (con sus argumentos) comienza el primer bloque catch; la macro **AND_CATCH** comienza los bloques catch subsiguientes y la macro **END_CATCH** termina la secuencia de bloques catch.

   Con las palabras clave, la palabra clave **catch** (con su declaración de excepción) comienza cada bloque catch. No hay contraparte a la macro **END_CATCH;** el bloque catch termina con su llave de cierre.

3. La expresión throw:

   Las macros usan **THROW_LAST** para volver a iniciar la excepción actual. La palabra clave **throw,** sin argumento, tiene el mismo efecto.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Hacer la conversión

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Para convertir código mediante macros para usar las palabras clave de control de excepciones de C++

1. Busque todas las apariciones de las macros MFC **TRY**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**y **THROW_LAST**.

2. Reemplace o elimine todas las apariciones de las siguientes macros:

   **PRUEBA** (Reemplazarlo con **try**)

   **CATCH** (Reemplazarlo con **catch)**

   **AND_CATCH** (Reemplazarlo con **catch)**

   **END_CATCH** (Eliminarlo)

   **THROW** (Reemplazarlo con **throw**)

   **THROW_LAST** (Reemplazarlo con **throw**)

3. Modifique los argumentos de macro para que formen declaraciones de excepción válidas.

   Por ejemplo, cambie

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifique el código en los bloques catch para que elimine los objetos de excepción según sea necesario. Para obtener más información, consulte el artículo [Excepciones: captura y eliminación](../mfc/exceptions-catching-and-deleting-exceptions.md)de excepciones .

Este es un ejemplo de código de control de excepciones mediante macros de excepción MFC. Tenga en cuenta que, dado que el `e` código del ejemplo siguiente utiliza las macros, la excepción se elimina automáticamente:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

El código del ejemplo siguiente utiliza las palabras clave de excepción C+++ , por lo que la excepción debe eliminarse explícitamente:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Para obtener más información, vea [Excepciones: uso de macros MFC y excepciones C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)<br/>
