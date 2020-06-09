---
title: Control de excepciones en MFC
ms.date: 11/19/2019
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
ms.openlocfilehash: ef827af413513d1a1753f84b1cb69a66f41f690c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618851"
---
# <a name="exception-handling-in-mfc"></a>Control de excepciones en MFC

En este artículo se explican los mecanismos de control de excepciones disponibles en MFC. Hay dos mecanismos disponibles:

- Excepciones de C++, disponibles en la versión 3,0 de MFC y versiones posteriores

- Macros de excepción de MFC, disponibles en las versiones 1,0 y posteriores de MFC

Si está escribiendo una nueva aplicación con MFC, debe utilizar el mecanismo de C++. Puede usar el mecanismo basado en macros si la aplicación existente ya usa ese mecanismo en gran medida.

Puede convertir fácilmente el código existente para usar excepciones de C++ en lugar de las macros de excepción de MFC. Las ventajas de convertir el código y las directrices para hacerlo se describen en el artículo [excepciones: convertir desde macros de excepción de MFC](exceptions-converting-from-mfc-exception-macros.md).

Si ya ha desarrollado una aplicación mediante las macros de excepción de MFC, puede seguir usando estas macros en el código existente, al tiempo que usa excepciones de C++ en el código nuevo. El artículo [excepciones: los cambios en las macros de excepción en la versión 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md) proporcionan instrucciones para hacerlo.

> [!NOTE]
> Para habilitar el control de excepciones de C++ en el código, seleccione Habilitar excepciones de C++ en la página generación de código en la carpeta C/C++ del cuadro de diálogo [páginas de propiedades](../build/reference/property-pages-visual-cpp.md) del proyecto o use la opción del compilador [/EHsc](../build/reference/eh-exception-handling-model.md) .

En este artículo se tratan los temas siguientes:

- [cuándo se utilizan excepciones](#_core_when_to_use_exceptions)

- [Compatibilidad con excepciones de MFC](#_core_mfc_exception_support)

- [Más información sobre las excepciones](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Cuándo usar excepciones

Se pueden producir tres categorías de resultados cuando se llama a una función durante la ejecución del programa: ejecución normal, ejecución errónea o ejecución anómala. Cada categoría se describe a continuación.

- Ejecución normal

   La función puede ejecutarse con normalidad y devolver. Algunas funciones devuelven un código de resultado al llamador, que indica el resultado de la función. Los códigos de resultado posibles se definen estrictamente para la función y representan el intervalo de resultados posibles de la función. El código de resultado puede indicar que se ha realizado correctamente o se ha producido un error, o incluso puede indicar un tipo determinado de error que se encuentra dentro del intervalo normal de expectativas. Por ejemplo, una función de estado de archivo puede devolver un código que indica que el archivo no existe. Tenga en cuenta que el término "código de error" no se usa porque un código de resultado representa uno de los muchos resultados esperados.

- Ejecución errónea

   El autor de la llamada comete algún error al pasar argumentos a la función o llama a la función en un contexto inadecuado. Esta situación provoca un error y se debe detectar mediante una aserción durante el desarrollo del programa. (Para obtener más información sobre las aserciones, vea [aserciones de C/C++](/visualstudio/debugger/c-cpp-assertions)).

- Ejecución anómala

   La ejecución anómala incluye situaciones en las que las condiciones que se encuentran fuera del control del programa, como la falta de memoria o los errores de e/s, están influyendo en el resultado de la función. Las situaciones anómalas deben controlarse mediante la detección y el inicio de excepciones.

El uso de excepciones es especialmente adecuado para la ejecución anómala.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Compatibilidad con excepciones de MFC

Tanto si usa las excepciones de C++ directamente como si usa las macros de excepción de MFC, utilizará la [clase CException](reference/cexception-class.md) u `CException` objetos derivados de que el marco de trabajo o la aplicación puedan producir.

En la tabla siguiente se muestran las excepciones predefinidas proporcionadas por MFC.

|Exception (clase)|Significado|
|---------------------|-------------|
|[CMemoryException (clase)](reference/cmemoryexception-class.md)|Memoria insuficiente|
|[CFileException (clase)](reference/cfileexception-class.md)|Excepción de archivo|
|[Clase CArchiveException](reference/carchiveexception-class.md)|Excepción de archivo/serialización|
|[Clase CNotSupportedException](reference/cnotsupportedexception-class.md)|Respuesta a la solicitud de servicio no admitido|
|[Clase CResourceException](reference/cresourceexception-class.md)|Excepción de asignación de recursos de Windows|
|[CDaoException (clase)](reference/cdaoexception-class.md)|Excepciones de base de datos (clases DAO)|
|[CDBException (clase)](reference/cdbexception-class.md)|Excepciones de base de datos (clases ODBC)|
|[Clase COleException](reference/coleexception-class.md)|excepciones OLE|
|[COleDispatchException (clase)](reference/coledispatchexception-class.md)|Excepciones de dispatch (Automation)|
|[CUserException (clase)](reference/cuserexception-class.md)|Excepción que alerta al usuario con un cuadro de mensaje y, a continuación, inicia una [clase CException](reference/cexception-class.md) genérica|

Desde la versión 3.0, MFC ha utilizado las excepciones de C++ pero sigue admitiendo sus anteriores macros de control de excepciones, que son similares a las excepciones de C++ en su forma. Aunque estas macros no son recomendables para nueva programación, todavía se siguen admitiendo por razones de compatibilidad con versiones anteriores. En los programas que ya utilizan las macros, también puede utilizar libremente las excepciones de C++. Durante el preprocesamiento, las macros se evalúan como las palabras clave de control de excepciones definidas en la implementación de MSVC del lenguaje C++ a partir de Visual C++ versión 2,0. Puede dejar las macros de excepciones existentes en su sitio mientras empieza a utilizar las excepciones de C++. Para obtener información sobre cómo mezclar macros y el control de excepciones de C++ y sobre cómo convertir código anterior para que use el nuevo mecanismo, vea los artículos [excepciones: usar macros de MFC y excepciones](exceptions-using-mfc-macros-and-cpp-exceptions.md) y excepciones de C++ [: convertir de macros de excepciones de MFC](exceptions-converting-from-mfc-exception-macros.md). Las macros de excepciones de MFC anteriores, si todavía las utiliza, se evalúan como palabras clave de excepciones de C++. Vea [excepciones: cambios en las macros de excepción en la versión 3,0](exceptions-changes-to-exception-macros-in-version-3-0.md). MFC no admite directamente los controladores de excepciones estructuradas (SEH) de Windows NT, como se describe en [control de excepciones estructurado](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Más información sobre las excepciones

En los siguientes artículos se explica el uso de la biblioteca MFC para la entrega de excepciones:

- [Excepciones: Detectar y eliminar excepciones](exceptions-catching-and-deleting-exceptions.md)

- [Excepciones: Examinar contenidos de excepciones](exceptions-examining-exception-contents.md)

- [Excepciones: Liberar objetos en las excepciones](exceptions-freeing-objects-in-exceptions.md)

- [Excepciones: Iniciar excepciones desde sus propias funciones](exceptions-throwing-exceptions-from-your-own-functions.md)

- [Excepciones: Excepciones de base de datos](exceptions-database-exceptions.md)

- [Excepciones: Excepciones OLE](exceptions-ole-exceptions.md)

En los siguientes artículos se comparan las macros de excepción de MFC con las palabras clave de excepción de C++ y se explica cómo se puede adaptar el código:

- [Excepciones: Cambios en las macros de excepción en la versión 3.0](exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Excepciones: Convertir desde macros de excepciones de MFC](exceptions-converting-from-mfc-exception-macros.md)

- [Excepciones: Usar macros de MFC y excepciones de C++](exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Consulte también

[Procedimientos recomendados de C++ moderno para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Cómo: crear clases de excepción personalizadas](https://go.microsoft.com/fwlink/p/?linkid=128045)
