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
ms.openlocfilehash: 8a936a0af9927aa0dc453a93c98676a77f4ad6dc
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621764"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Excepciones: Convertir desde macros de excepciones de MFC

Este es un tema avanzado.

En este artículo se explica cómo convertir el código existente escrito con macros de Microsoft Foundation Class ( **try**, **catch**, **Throw**, etc.) para usar las palabras clave de control de excepciones de C++ **try**, **catch**y **Throw**. Contenido de los temas:

- [Ventajas de la conversión](#_core_advantages_of_converting)

- [Convertir código con macros de excepción para usar excepciones de C++](#_core_doing_the_conversion)

## <a name="advantages-of-converting"></a><a name="_core_advantages_of_converting"></a>Ventajas de la conversión

Probablemente no sea necesario convertir el código existente, aunque debe tener en cuenta las diferencias entre las implementaciones de macros en la versión 3,0 de MFC y las implementaciones en versiones anteriores. Estas diferencias y los cambios subsiguientes en el comportamiento del código se describen en [excepciones: cambios en las macros de excepción en la versión 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md).

Las principales ventajas de la conversión son:

- El código que usa las palabras clave de control de excepciones de C++ se compila en un poco más pequeño. EXE o. DLL.

- Las palabras clave de control de excepciones de C++ son más versátiles: pueden controlar las excepciones de cualquier tipo de datos que se pueda copiar (**int**, **float**, **Char**, etc.), mientras que las macros controlan las excepciones solo de la clase `CException` y las clases derivadas de ella.

La diferencia principal entre las macros y las palabras clave es que el código que usa las macros "automáticamente" elimina una excepción detectada cuando la excepción sale del ámbito. El código que usa las palabras clave no, por lo que debe eliminar explícitamente una excepción detectada. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

Otra diferencia es la sintaxis. La sintaxis de las macros y las palabras clave difiere en tres aspectos:

1. Argumentos de macro y declaraciones de excepción:

   Una invocación de macro **catch** tiene la siguiente sintaxis:

   **Catch (** *exception_class*, *exception_object_pointer_name* **)**

   Observe la coma entre el nombre de clase y el nombre de puntero de objeto.

   La declaración de excepción de la palabra clave **catch** usa esta sintaxis:

   **catch (** *exception_type* *exception_name* **)**

   Esta instrucción de declaración de excepción indica el tipo de excepción que controla el bloque catch.

2. Delimitación de bloques catch:

   Con las macros, la macro **catch** (con sus argumentos) comienza el primer bloque catch; la macro **AND_CATCH** comienza los bloques Catch posteriores y la macro **END_CATCH** finaliza la secuencia de bloques Catch.

   Con las palabras clave, la palabra clave **catch** (con su declaración de excepción) comienza cada bloque catch. No hay ningún homólogo para la macro **END_CATCH** ; el bloque catch termina con la llave de cierre.

3. Expresión Throw:

   Las macros usan **THROW_LAST** para volver a producir la excepción actual. La palabra clave **Throw** , sin ningún argumento, tiene el mismo efecto.

## <a name="doing-the-conversion"></a><a name="_core_doing_the_conversion"></a>Realizar la conversión

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Para convertir código mediante macros para usar las palabras clave de control de excepciones de C++

1. Busque todas las apariciones de las macros de MFC **try**, **catch**, **AND_CATCH**, **END_CATCH**, **Throw**y **THROW_LAST**.

2. Reemplace o elimine todas las apariciones de las siguientes macros:

   **Try** (reemplácelo por **try**)

   **Catch** (reemplácelo por **catch**)

   **AND_CATCH** (reemplácelo por **catch**)

   **END_CATCH** (eliminarlo)

   **Throw** (reemplácelo por **Throw**)

   **THROW_LAST** (reemplácelo por **Throw**)

3. Modifique los argumentos de la macro para que formen declaraciones de excepción válidas.

   Por ejemplo, cambie

   [!code-cpp[NVC_MFCExceptions#6](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   to

   [!code-cpp[NVC_MFCExceptions#7](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifique el código en los bloques catch para que elimine los objetos de excepción según sea necesario. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md).

Este es un ejemplo de código de control de excepciones que usa macros de excepción de MFC. Tenga en cuenta que, dado que el código del ejemplo siguiente usa las macros, la excepción `e` se elimina automáticamente:

[!code-cpp[NVC_MFCExceptions#8](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

El código del ejemplo siguiente usa las palabras clave de excepción de C++, por lo que la excepción se debe eliminar explícitamente:

[!code-cpp[NVC_MFCExceptions#9](codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Para obtener más información, vea [excepciones: usar macros de MFC y excepciones de C++](exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Consulte también

[Control de excepciones](exception-handling-in-mfc.md)<br/>
