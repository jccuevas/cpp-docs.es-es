---
title: 'Excepciones: Convertir desde Macros de excepciones de MFC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a386de558730e12bb8cf40da250c1d04dd4ff37a
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931123"
---
# <a name="exceptions-converting-from-mfc-exception-macros"></a>Excepciones: Convertir desde macros de excepciones de MFC
Se trata de un tema avanzado.  
  
 Este artículo explica cómo convertir el código existente escrito con macros de Microsoft Foundation Class: **intente**, **CATCH**, **THROW**, y así sucesivamente, para usar el control de excepciones de C++ palabras clave **intente**, **catch**, y **producir**. Entre los temas se incluyen los siguientes:  
  
-   [Ventajas de conversión](#_core_advantages_of_converting)  
  
-   [Convertir código con las macros de excepción para utilizar excepciones de C++](#_core_doing_the_conversion)  
  
##  <a name="_core_advantages_of_converting"></a> Ventajas de la conversión  
 Probablemente no necesitará convertir el código existente, aunque debe ser consciente de las diferencias entre las implementaciones de macros en la versión 3.0 de MFC y las implementaciones en las versiones anteriores. Estas diferencias y los cambios posteriores en el comportamiento del código se tratan en [excepciones: cambios en las Macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md).  
  
 Las principales ventajas de conversión son:  
  
-   Código que utiliza las palabras clave de control de excepciones de C++ se compila a un ligeramente inferiores. EXE o. DLL.  
  
-   Las palabras clave de control de excepciones de C++ son más versátiles: puede controlar excepciones de cualquier tipo de datos que se puede copiar (**int**, **float**, **char**, etc.), mientras que el macros de controlan las excepciones sólo de la clase `CException` y sus clases derivadas.  
  
 La diferencia principal entre las macros y las palabras clave es que el código mediante las macros "automáticamente" elimina una excepción detectada cuando ésta sale del ámbito. Código que utiliza las palabras clave no es así, por lo que se debe eliminar explícitamente una excepción detectada. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Otra diferencia es la sintaxis. La sintaxis de macros y las palabras clave se diferencia en tres aspectos:  
  
1.  Los argumentos de macro y las declaraciones de excepción:  
  
     A **CATCH** llamada de macro tiene la siguiente sintaxis:  
  
     **CATCH (** *exception_class*, *exception_object_pointer_name* **)**  
  
     Tenga en cuenta el punto y coma entre el nombre de clase y el nombre del puntero de objeto.  
  
     La declaración de excepción para la **catch** palabra clave utiliza esta sintaxis:  
  
     **catch (** *exception_type* *exception_name ***)**  
  
     Esta instrucción de declaración de excepción indica el tipo de excepción catch bloquear identificadores.  
  
2.  Delimitación de los bloques catch:  
  
     Con las macros, la **CATCH** macro (con sus argumentos) comienza el primer bloque catch; el **AND_CATCH** macro comienza los bloques catch subsiguientes y el **END_CATCH** (macro) finaliza la secuencia de bloques catch.  
  
     Con las palabras clave, el **catch** palabra clave (con su declaración de excepción) comienza cada bloque catch. No hay ningún equivalente para la **END_CATCH** macro; catch bloquear termina con la llave de cierre.  
  
3.  La expresión throw:  
  
     Usan las macros **THROW_LAST** para volver a producir la excepción actual. El **throw** (palabra clave), sin ningún argumento, tiene el mismo efecto.  
  
##  <a name="_core_doing_the_conversion"></a> Realizar la conversión  
  
#### <a name="to-convert-code-using-macros-to-use-the-c-exception-handling-keywords"></a>Para convertir código que utiliza las macros al usar las palabras clave de control de excepciones de C++  
  
1.  Buscar todas las apariciones de las macros MFC **intente**, **CATCH**, **AND_CATCH**, **END_CATCH**, **THROW**, y **THROW_LAST**.  
  
2.  Reemplazar o eliminar todas las apariciones de las macros siguientes:  
  
     **Intente** (reemplácela con **intente**)  
  
     **DETECTAR** (reemplácela con **catch**)  
  
     **AND_CATCH** (reemplácela con **catch**)  
  
     **END_CATCH** (eliminar)  
  
     **INICIAR** (reemplácela con **throw**)  
  
     **THROW_LAST** (reemplácela con **throw**)  
  
3.  Modifique los argumentos de macro para que formen declaraciones de excepción válidas.  
  
     Por ejemplo, cambiar  
  
     [!code-cpp[NVC_MFCExceptions#6](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_1.cpp)]  
  
     por  
  
     [!code-cpp[NVC_MFCExceptions#7](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_2.cpp)]  
  
4.  Modifique el código en los bloques catch, por lo que elimina los objetos de excepción según sea necesario. Para obtener más información, vea el artículo [excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
 Este es un ejemplo de código de control de excepciones con macros de excepciones de MFC. Tenga en cuenta que, dado que el código en el siguiente ejemplo utiliza las macros, la excepción `e` se elimina automáticamente:  
  
 [!code-cpp[NVC_MFCExceptions#8](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_3.cpp)]  
  
 El código en el ejemplo siguiente utiliza las palabras clave de excepciones de C++, por lo que se debe eliminar explícitamente la excepción:  
  
 [!code-cpp[NVC_MFCExceptions#9](../mfc/codesnippet/cpp/exceptions-converting-from-mfc-exception-macros_4.cpp)]  
  
 Para obtener más información, consulte [excepciones: utilizar Macros de MFC y las excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md).  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)

