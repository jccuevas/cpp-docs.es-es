---
title: 'Excepciones: Convertir desde Macros de excepción de MFC'
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
ms.openlocfilehash: 59b83438d5341fd6a139af64a2f365a739438741
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394512"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Excepciones: Convertir desde Macros de excepción de MFC

Se trata de un tema avanzado.

En este artículo se explica cómo convertir el código existente escrito con macros de Microsoft Foundation Class: **intente**, **CATCH**, **THROW**, y así sucesivamente, al usar el control de excepciones de C++ palabras clave **intente**, **catch**, y **throw**. Entre los temas se incluyen los siguientes:

- [Ventajas de conversión](#_core_advantages_of_converting)

- [Convertir código de macros de excepción para usar las excepciones de C++](#_core_doing_the_conversion)

##  <a name="_core_advantages_of_converting"></a> Ventajas de la conversión

Probablemente no necesitará convertir el código existente, aunque debe tener en cuenta las diferencias entre las implementaciones de macros en la versión 3.0 de MFC y las implementaciones en las versiones anteriores. Estas diferencias y los cambios posteriores en el comportamiento del código se tratan en [excepciones: Cambios en las Macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).

Las principales ventajas de conversión son:

- Código que utiliza las palabras clave de control de excepciones de C++ se compila a ligeramente inferiores. EXE o. ARCHIVO DLL.

- El C++ son más versátiles palabras clave de control de excepciones: Puede controlar excepciones de cualquier tipo de datos que se puede copiar (**int**, **float**, **char**, y así sucesivamente), mientras que las macros de controlan las excepciones solo de la clase `CException` y sus clases derivadas.

La principal diferencia entre las macros y las palabras clave es que el código mediante las macros "automáticamente" elimina una excepción detectada cuando ésta sale del ámbito. El código mediante las palabras clave no es así, por lo que debe eliminar explícitamente una excepción detectada. Para obtener más información, vea el artículo [excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

Otra diferencia es la sintaxis. La sintaxis de macros y palabras clave se diferencia en tres aspectos:

1. Argumentos de macro y las declaraciones de excepción:

   Un **CATCH** llamada de macro tiene la siguiente sintaxis:

   **CATCH(** *exception_class*, *exception_object_pointer_name* **)**

   Tenga en cuenta la coma entre el nombre de clase y el nombre del puntero de objeto.

   La declaración de excepción para el **catch** palabra clave utiliza esta sintaxis:

   **catch(** *exception_type* *exception_name* **)**

   Esta instrucción de declaración de excepción indica el tipo de excepción catch identificadores de bloque.

2. Delimitación de bloques catch:

   Con las macros, la **CATCH** macros (con sus argumentos) comienza el primer bloque catch; el **AND_CATCH** macro comienza bloques catch posteriores y el **END_CATCH** macro finaliza la secuencia de bloques catch.

   Con las palabras clave, el **catch** cada bloque catch comienza la palabra clave (con su declaración de excepción). No hay ningún equivalente a la **END_CATCH** macro; finaliza con la llave de cierre de bloque catch.

3. La expresión throw:

   Usan las macros **THROW_LAST** para volver a iniciar la excepción actual. El **throw** palabra clave, sin ningún argumento, tiene el mismo efecto.

##  <a name="_core_doing_the_conversion"></a> Realizar la conversión

#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Para convertir código mediante las macros para usar las palabras clave de control de excepciones de C++

1. Buscar todas las apariciones de las macros MFC **intente**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**, y **THROW_LAST**.

2. Reemplazar o eliminar todas las apariciones de las macros siguientes:

   **Pruebe** (reemplazarlo **intente**)

   **DETECTAR** (reemplazarlo **catch**)

   **AND_CATCH** (reemplazarlo **catch**)

   **END_CATCH** (eliminar)

   **PRODUCIR** (reemplazarlo **throw**)

   **THROW_LAST** (reemplazarlo **throw**)

3. Modifique los argumentos de macro para que formen declaraciones de excepción válidas.

   Por ejemplo, cambiar

   [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]

   por

   [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]

4. Modifique el código en los bloques catch para que elimina los objetos de excepción según sea necesario. Para obtener más información, vea el artículo [excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).

Este es un ejemplo de código de control de excepciones con las macros de excepción de MFC. Tenga en cuenta que dado que el código en el ejemplo siguiente utiliza las macros, la excepción `e` se elimina automáticamente:

[!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]

El código en el ejemplo siguiente utiliza las palabras clave de excepciones de C++, por lo que se debe eliminar explícitamente la excepción:

[!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]

Para obtener más información, consulte [excepciones: Uso de macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).

## <a name="see-also"></a>Vea también

[Control de excepciones](../mfc/exception-handling-in-mfc.md)<br/>
