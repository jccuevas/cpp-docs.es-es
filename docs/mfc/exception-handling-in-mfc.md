---
title: Control de excepciones en MFC
ms.date: 11/04/2016
helpviewer_keywords:
- DAO [MFC], exceptions
- assertions [MFC], When to use exceptions
- exception handling [MFC], MFC
- resource allocation exception
- resources [MFC], allocating
- keywords [MFC], exception handling
- errors [MFC], detected by assertions
- ODBC exceptions [MFC]
- serialization [MFC], exceptions
- Automation [MFC], exceptions
- exception macros [MFC]
- predefined exceptions [MFC]
- C++ exception handling [MFC], enabling
- C++ exception handling [MFC], MFC applications
- requests for unsupported services [MFC]
- database exceptions [MFC]
- archive exceptions [MFC]
- MFC, exceptions
- C++ exception handling [MFC], types of
- macros [MFC], exception handling
- abnormal program execution [MFC]
- OLE exceptions [MFC], MFC exception handling
- error handling [MFC], exceptions and
- class libraries [MFC], exception support
- exceptions [MFC], MFC macros vs. C++ keywords
- memory [MFC], out-of-memory exceptions
- Windows [MFC], resource allocation exceptions
- macros [MFC], MFC exception macros
- function calls [MFC], results
- out-of-memory exceptions [MFC]
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
ms.openlocfilehash: e8c0f1feba566ef9b961edcfacb9124830f9851d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508622"
---
# <a name="exception-handling-in-mfc"></a>Control de excepciones en MFC

En este artículo se explican los mecanismos de control de excepciones disponibles en MFC. Hay dos mecanismos disponibles:

- C++excepciones, disponibles en la versión 3,0 de MFC y versiones posteriores

- Macros de excepción de MFC, disponibles en las versiones 1,0 y posteriores de MFC

Si está escribiendo una nueva aplicación con MFC, debe utilizar el C++ mecanismo. Puede usar el mecanismo basado en macros si la aplicación existente ya usa ese mecanismo en gran medida.

Puede convertir fácilmente el código existente para usar C++ excepciones en lugar de las macros de excepción de MFC. Las ventajas de convertir el código y las directrices para hacerlo se describen en el [artículo excepciones: Convertir a partir de macros](../mfc/exceptions-converting-from-mfc-exception-macros.md)de excepción de MFC.

Si ya ha desarrollado una aplicación mediante las macros de excepción de MFC, puede seguir usando estas macros en el código existente, mientras usa C++ excepciones en el código nuevo. El artículo [excepciones: Los cambios en las macros de excepción](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) de la versión 3,0 proporcionan instrucciones para hacerlo.

> [!NOTE]
>  Para habilitar C++ el control de excepciones en el código, C++ seleccione Habilitar excepciones en la página generación de código enC++ la carpeta C/del cuadro de diálogo [páginas de propiedades](../build/reference/property-pages-visual-cpp.md) del proyecto o use la opción del compilador [/EHsc](../build/reference/eh-exception-handling-model.md) .

En este artículo se tratan los siguientes temas:

- [Cuándo usar excepciones](#_core_when_to_use_exceptions)

- [Compatibilidad con excepciones de MFC](#_core_mfc_exception_support)

- [Más información sobre las excepciones](#_core_further_reading_about_exceptions)

##  <a name="_core_when_to_use_exceptions"></a>Cuándo usar excepciones

Se pueden producir tres categorías de resultados cuando se llama a una función durante la ejecución del programa: ejecución normal, ejecución errónea o ejecución anómala. Cada categoría se describe a continuación.

- Ejecución normal

   La función puede ejecutarse con normalidad y devolver. Algunas funciones devuelven un código de resultado al llamador, que indica el resultado de la función. Los códigos de resultado posibles se definen estrictamente para la función y representan el intervalo de resultados posibles de la función. El código de resultado puede indicar que se ha realizado correctamente o se ha producido un error, o incluso puede indicar un tipo determinado de error que se encuentra dentro del intervalo normal de expectativas. Por ejemplo, una función de estado de archivo puede devolver un código que indica que el archivo no existe. Tenga en cuenta que el término "código de error" no se usa porque un código de resultado representa uno de los muchos resultados esperados.

- Ejecución errónea

   El autor de la llamada comete algún error al pasar argumentos a la función o llama a la función en un contexto inadecuado. Esta situación provoca un error y se debe detectar mediante una aserción durante el desarrollo del programa. (Para obtener más información sobre las aserciones, vea [CC++ /aserciones](/visualstudio/debugger/c-cpp-assertions)).

- Ejecución anómala

   La ejecución anómala incluye situaciones en las que las condiciones que se encuentran fuera del control del programa, como la falta de memoria o los errores de e/s, están influyendo en el resultado de la función. Las situaciones anómalas deben controlarse mediante la detección y el inicio de excepciones.

El uso de excepciones es especialmente adecuado para la ejecución anómala.

##  <a name="_core_mfc_exception_support"></a>Compatibilidad con excepciones de MFC

Tanto si usa las C++ excepciones directamente como si usa las macros de excepción de MFC, utilizará la `CException` [clase CException](../mfc/reference/cexception-class.md) u objetos derivados de que el marco de trabajo o la aplicación puedan producir.

En la tabla siguiente se muestran las excepciones predefinidas proporcionadas por MFC.

|Exception (clase)|Significado|
|---------------------|-------------|
|[CMemoryException (clase)](../mfc/reference/cmemoryexception-class.md)|Memoria insuficiente|
|[CFileException (clase)](../mfc/reference/cfileexception-class.md)|Excepción de archivo|
|[CArchiveException (clase)](../mfc/reference/carchiveexception-class.md)|Excepción de archivo/serialización|
|[CNotSupportedException (clase)](../mfc/reference/cnotsupportedexception-class.md)|Respuesta a la solicitud de servicio no admitido|
|[CResourceException (clase)](../mfc/reference/cresourceexception-class.md)|Excepción de asignación de recursos de Windows|
|[CDaoException (clase)](../mfc/reference/cdaoexception-class.md)|Excepciones de base de datos (clases DAO)|
|[CDBException (clase)](../mfc/reference/cdbexception-class.md)|Excepciones de base de datos (clases ODBC)|
|[COleException (clase)](../mfc/reference/coleexception-class.md)|excepciones OLE|
|[COleDispatchException (clase)](../mfc/reference/coledispatchexception-class.md)|Excepciones de dispatch (Automation)|
|[CUserException (clase)](../mfc/reference/cuserexception-class.md)|Excepción que alerta al usuario con un cuadro de mensaje y, a continuación, inicia una [clase CException](../mfc/reference/cexception-class.md) genérica|

> [!NOTE]
>  MFC admite las C++ excepciones y las macros de excepción de MFC. MFC no admite directamente los controladores de excepciones estructuradas (SEH) de Windows NT, como se describe en [control de excepciones estructurado](/windows/win32/debug/structured-exception-handling).

##  <a name="_core_further_reading_about_exceptions"></a>Más información sobre las excepciones

En los siguientes artículos se explica el uso de la biblioteca MFC para la entrega de excepciones:

- [Excepciones: detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md)

- [Excepciones: liberar objetos en excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Excepciones: Iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Excepciones: excepciones de la base de datos](../mfc/exceptions-database-exceptions.md)

- [Excepciones: excepciones OLE](../mfc/exceptions-ole-exceptions.md)

En los siguientes artículos se comparan las macros C++ de excepción de MFC con las palabras clave de excepción y se explica cómo se puede adaptar el código:

- [Excepciones: Cambios en las macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Excepciones: Convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Excepciones: Uso de macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Vea también

[Control de excepciones de C++](../cpp/cpp-exception-handling.md)<br/>
[Cómo: Crear mis propias clases de excepción personalizadas](https://go.microsoft.com/fwlink/p/?linkid=128045)
