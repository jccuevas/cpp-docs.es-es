---
title: Control de excepciones en MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0792ddf067f6289d612a9adb0c8ffeaf8e554ed6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-in-mfc"></a>Control de excepciones en MFC
Este artículo explica los mecanismos de control de excepciones disponibles en MFC. Existen dos mecanismos:  
  
-   Excepciones de C++, disponibles en la versión MFC 3.0 y versiones posteriores  
  
-   Las macros de excepción de MFC, disponibles en versiones MFC 1.0 y versiones posteriores  
  
 Si va a escribir una nueva aplicación mediante MFC, debe usar el mecanismo de C++. Puede utilizar el mecanismo basado en macros si una aplicación existente ya utiliza ese mecanismo ampliamente.  
  
 Puede convertir con facilidad el código existente para usar las excepciones de C++ en lugar de las macros de excepción de MFC. Ventajas de convertir el código y las instrucciones para hacerlo se describen en el artículo [excepciones: convertir desde Macros de excepción de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Si ya ha desarrollado una aplicación mediante las macros de excepción de MFC, puede continuar utilizando estas macros en el código existente, mientras usa las excepciones de C++ en el código nuevo. El artículo [excepciones: cambios en las Macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) se proporcionan instrucciones para hacerlo.  
  
> [!NOTE]
>  Para habilitar en el código de control de excepciones de C++, seleccione Habilitar excepciones de C++ en la página generación de código en la carpeta C/C ++ del proyecto [páginas de propiedades](../ide/property-pages-visual-cpp.md) cuadro de diálogo, o use la opción del compilador/GX. El valor predeterminado es /GX-, lo que deshabilita el control de excepciones.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Cuándo utilizar excepciones](#_core_when_to_use_exceptions)  
  
-   [Compatibilidad con excepciones de MFC](#_core_mfc_exception_support)  
  
-   [Obtener más información sobre las excepciones](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> Cuándo utilizar excepciones  
 Tres categorías de resultados pueden producirse cuando se llama a una función durante la ejecución del programa: ejecución normal, ejecución con errores o ejecución anormal. A continuación se describe cada categoría.  
  
-   Ejecución normal  
  
     La función puede ejecutarse con normalidad y devolver. Algunas funciones devuelven un código de resultado para el llamador, que indica el resultado de la función. Los códigos de resultado posibles estrictamente definidos para la función y representan el intervalo de los posibles resultados de la función. El código de resultado puede indicar el éxito o fracaso o incluso puede indicar un determinado tipo de error que está dentro del intervalo normal de las expectativas. Por ejemplo, una función de estado de archivo puede devolver un código que indica que el archivo no existe. Tenga en cuenta que el término "código de error" no se utiliza como un código de resultado representa uno de muchos resultados esperados.  
  
-   Ejecución con errores  
  
     El llamador comete algún error al pasar argumentos a la función o llama a la función en un contexto inadecuado. Esta situación produce un error y debe ser detectada por una aserción durante el desarrollo del programa. (Para obtener más información sobre las aserciones, vea [aserciones de C/C ++](/visualstudio/debugger/c-cpp-assertions).)  
  
-   Ejecución anómala  
  
     Ejecución anormal incluye situaciones donde condiciones fuera del control del programa, como memoria insuficiente o errores de E/S, influyen en el resultado de la función. Situaciones anómalas deben controlarse detectando e iniciando excepciones.  
  
 Utilizar excepciones resulta especialmente indicado para la ejecución anormal.  
  
##  <a name="_core_mfc_exception_support"></a> Compatibilidad con excepciones de MFC  
 Si se utilizan las excepciones de C++ directamente o las macros de excepción de MFC, utilizará [CException (clase)](../mfc/reference/cexception-class.md) o `CException`-objetos que se pueden iniciar mediante el marco de trabajo o la aplicación derivados.  
  
 La siguiente tabla muestra las excepciones predefinidas proporcionadas por MFC.  
  
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
|[COleDispatchException (clase)](../mfc/reference/coledispatchexception-class.md)|Excepciones de envío (automatización)|  
|[CUserException (clase)](../mfc/reference/cuserexception-class.md)|Excepción que alerta al usuario con un cuadro de mensaje, a continuación, inicia un tipo genérico [CException (clase)](../mfc/reference/cexception-class.md)|  
  
> [!NOTE]
>  MFC admite tanto las excepciones de C++ y las macros de excepción de MFC. MFC no admite directamente la estructura de Windows NT controladores de excepciones (SEH), como se describe en [Structured Exception Handling](http://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a> Obtener más información sobre las excepciones  
 Los siguientes artículos explican el uso de la biblioteca MFC para entregar de excepción:  
  
-   [Excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Excepciones: Liberar objetos en las excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Excepciones: Iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Excepciones: Excepciones de base de datos](../mfc/exceptions-database-exceptions.md)  
  
-   [Excepciones: Excepciones OLE](../mfc/exceptions-ole-exceptions.md)  
  
 Los artículos siguientes comparan las macros de excepción de MFC con las palabras clave de excepción de C++ y explican cómo puede adaptar el código:  
  
-   [Excepciones: Cambios en las macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Excepciones: Convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Excepciones: Usar macros de MFC y excepciones de C++](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## <a name="see-also"></a>Vea también  
 [Control de excepciones de C++](../cpp/cpp-exception-handling.md)   
 [Cómo: crear Mis propio clases de excepción personalizadas](http://go.microsoft.com/fwlink/p/?linkid=128045)

