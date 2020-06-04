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
ms.openlocfilehash: d339ec98dabc6cb24fc7106c4c7238cd6a14a71b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365530"
---
# <a name="exception-handling-in-mfc"></a>Control de excepciones en MFC

En este artículo se explican los mecanismos de control de excepciones disponibles en MFC. Hay dos mecanismos disponibles:

- Excepciones C++, disponibles en MFC versión 3.0 y posteriores

- Las macros de excepción MFC, disponibles en las versiones 1.0 y posteriores de MFC

Si está escribiendo una nueva aplicación con MFC, debe usar el mecanismo C++. Puede usar el mecanismo basado en macros si la aplicación existente ya utiliza ese mecanismo ampliamente.

Puede convertir fácilmente el código existente para usar excepciones C++ en lugar de las macros de excepción MFC. Las ventajas de convertir el código y las directrices para hacerlo se describen en el artículo [Excepciones: conversión de](../mfc/exceptions-converting-from-mfc-exception-macros.md)macros de excepciones MFC .

Si ya ha desarrollado una aplicación mediante las macros de excepción MFC, puede seguir utilizando estas macros en el código existente, mientras usa excepciones De C++ en el nuevo código. El artículo [Excepciones: cambios en](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) macros de excepción en la versión 3.0 proporciona instrucciones para hacerlo.

> [!NOTE]
> Para habilitar el control de excepciones de C++ en el código, seleccione Habilitar excepciones C++ en la página Generación de código de la carpeta C/C++ del cuadro de diálogo [Páginas](../build/reference/property-pages-visual-cpp.md) de propiedades del proyecto o use la opción del compilador [/EHsc.](../build/reference/eh-exception-handling-model.md)

En este artículo se tratan los temas siguientes:

- [cuándo se utilizan excepciones](#_core_when_to_use_exceptions)

- [Compatibilidad con excepciones MFC](#_core_mfc_exception_support)

- [Lectura adicional sobre excepciones](#_core_further_reading_about_exceptions)

## <a name="when-to-use-exceptions"></a><a name="_core_when_to_use_exceptions"></a>Cuándo usar excepciones

Pueden producirse tres categorías de resultados cuando se llama a una función durante la ejecución del programa: ejecución normal, ejecución errónea o ejecución anormal. Cada categoría se describe a continuación.

- Ejecución normal

   La función puede ejecutarse normalmente y volver. Algunas funciones devuelven un código de resultado al autor de la llamada, que indica el resultado de la función. Los posibles códigos de resultado están estrictamente definidos para la función y representan el rango de posibles resultados de la función. El código de resultado puede indicar éxito o error o incluso puede indicar un tipo determinado de error que está dentro del intervalo normal de expectativas. Por ejemplo, una función de estado de archivo puede devolver un código que indica que el archivo no existe. Tenga en cuenta que el término "código de error" no se utiliza porque un código de resultado representa uno de los muchos resultados esperados.

- Ejecución errónea

   El llamador comete algún error al pasar argumentos a la función o llama a la función en un contexto inapropiado. Esta situación produce un error y debe detectarse mediante una aserción durante el desarrollo del programa. (Para obtener más información sobre las aserciones, consulte [Aserciones de C/C+.)](/visualstudio/debugger/c-cpp-assertions)

- Ejecución anormal

   La ejecución anormal incluye situaciones en las que las condiciones fuera del control del programa, como la memoria baja o los errores de E/S, están influyendo en el resultado de la función. Las situaciones anormales deben controlarse detectando y lanzando excepciones.

El uso de excepciones es especialmente adecuado para la ejecución anormal.

## <a name="mfc-exception-support"></a><a name="_core_mfc_exception_support"></a>Compatibilidad con excepciones MFC

Si usa las excepciones de C++ directamente o las macros `CException`de excepciones MFC, usará [CException Class](../mfc/reference/cexception-class.md) o -derived objetos que puede producir el marco de trabajo o la aplicación.

En la tabla siguiente se muestran las excepciones predefinidas proporcionadas por MFC.

|Exception (clase)|Significado|
|---------------------|-------------|
|[CMemoryException (clase)](../mfc/reference/cmemoryexception-class.md)|Fuera de memoria|
|[CFileException (clase)](../mfc/reference/cfileexception-class.md)|Excepción de archivo|
|[Clase CArchiveException](../mfc/reference/carchiveexception-class.md)|Excepción de archivo/serialización|
|[Clase CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)|Respuesta a la solicitud de servicio no compatible|
|[Clase CResourceException](../mfc/reference/cresourceexception-class.md)|Excepción de asignación de recursos de Windows|
|[Clase CDaoException](../mfc/reference/cdaoexception-class.md)|Excepciones de base de datos (clases DAO)|
|[CDBException (clase)](../mfc/reference/cdbexception-class.md)|Excepciones de base de datos (clases ODBC)|
|[Clase COleException](../mfc/reference/coleexception-class.md)|excepciones OLE|
|[COleDispatchException (clase)](../mfc/reference/coledispatchexception-class.md)|Excepciones de envío (automatización)|
|[CUserException (clase)](../mfc/reference/cuserexception-class.md)|Excepción que alerta al usuario con un cuadro de mensaje y, a continuación, produce una [clase CException](../mfc/reference/cexception-class.md) genérica|

Desde la versión 3.0, MFC ha utilizado las excepciones de C++ pero sigue admitiendo sus anteriores macros de control de excepciones, que son similares a las excepciones de C++ en su forma. Aunque estas macros no son recomendables para nueva programación, todavía se siguen admitiendo por razones de compatibilidad con versiones anteriores. En los programas que ya utilizan las macros, también puede utilizar libremente las excepciones de C++. Durante el preprocesamiento, las macros se evalúan como las palabras clave de control de excepciones definidas en la implementación de MSVC del lenguaje C++ a partir de Visual C++ versión 2.0. Puede dejar las macros de excepciones existentes en su sitio mientras empieza a utilizar las excepciones de C++. Para obtener información sobre la mezcla de macros y el control de excepciones de C++ y sobre la conversión de código antiguo para usar el nuevo mecanismo, vea los [artículos Excepciones: Uso](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) de macros MFC y Excepciones y excepciones de C++: [Conversión desde macros](../mfc/exceptions-converting-from-mfc-exception-macros.md)de excepciones MFC . Las macros de excepciones de MFC anteriores, si todavía las utiliza, se evalúan como palabras clave de excepciones de C++. Consulte [Excepciones: cambios en macros de excepciones en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md). MFC no admite directamente controladores de excepciones estructurados (SEH) de Windows NT, como se describe en [Control de excepciones estructurado](/windows/win32/debug/structured-exception-handling).

## <a name="further-reading-about-exceptions"></a><a name="_core_further_reading_about_exceptions"></a>Lectura adicional sobre excepciones

En los artículos siguientes se explica el uso de la biblioteca MFC para la entrega de excepciones:

- [Excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md)

- [Excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md)

- [Excepciones: Liberar objetos en las excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md)

- [Excepciones: Iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)

- [Excepciones: Excepciones de base de datos](../mfc/exceptions-database-exceptions.md)

- [Excepciones: Excepciones OLE](../mfc/exceptions-ole-exceptions.md)

En los artículos siguientes se comparan las macros de excepción MFC con las palabras clave de excepción C++ y se explica cómo puede adaptar el código:

- [Excepciones: Cambios en las macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)

- [Excepciones: Convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)

- [Excepciones: Usar macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)

## <a name="see-also"></a>Consulte también

[Prácticas recomendadas modernas de C++ para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Cómo puedo: Crear mis propias clases de excepción personalizadas](https://go.microsoft.com/fwlink/p/?linkid=128045)
