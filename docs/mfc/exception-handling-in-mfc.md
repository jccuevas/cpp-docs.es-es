---
title: "Control de excepciones en MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ejecución anómala del programa [C++]"
  - "excepciones del archivo [C++]"
  - "aserciones [C++], cuándo se utilizan excepciones"
  - "automatización [C++], excepciones"
  - "control de excepciones de C++, habilitar"
  - "control de excepciones de C++, MFC (aplicaciones)"
  - "control de excepciones de C++, tipos de"
  - "bibliotecas de clases [C++], compatibilidad de excepciones"
  - "DAO [C++], excepciones"
  - "excepciones de la base de datos [C++]"
  - "control de errores [C++], excepciones y"
  - "errores [C++], detectados por aserciones"
  - "control de excepciones [C++], MFC"
  - "macros de excepción [C++]"
  - "excepciones [C++], macros de MFC frente a palabras clave de C++"
  - "llamadas a funciones, resultados"
  - "palabras clave [C++], control de excepciones"
  - "macros [C++], control de excepciones"
  - "macros [C++], macros de excepción de MFC"
  - "memoria [C++], out_of_memory (excepciones)"
  - "MFC [C++], excepciones"
  - "excepciones ODBC [C++]"
  - "excepciones OLE [C++], control de excepciones de MFC"
  - "out_of_memory (excepciones) [C++]"
  - "excepciones predefinidas [C++]"
  - "solicitudes para servicios no admitidos"
  - "excepción de asignación de recursos"
  - "recursos [C++], asignar"
  - "serialización [C++], excepciones"
  - "Windows [C++], excepciones de asignación de recursos"
ms.assetid: 0926627d-2ba7-44a6-babe-d851a4a2517c
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Control de excepciones en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los mecanismos de control de excepciones disponibles en MFC.  Dos mecanismos disponibles:  
  
-   Excepciones de C\+\+, disponible en la versión 3.0 de MFC y posterior  
  
-   Las macros de excepción de MFC, disponible en las versiones 1.0 de MFC y posterior  
  
 Si escribe una nueva aplicación mediante MFC, debe utilizar el mecanismo de C\+\+.  Puede utilizar el mecanismo macro\- basado si la aplicación existente utiliza ya ese mecanismo ampliamente.  
  
 Puede convertir fácilmente código existente para utilizar excepciones de C\+\+ en lugar de las macros de excepción de MFC.  Las ventajas de convertir el código e instrucciones para ello se describen en el caso [Excepciones: Convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
 Si ha desarrollado ya una aplicación utilizando las macros de excepción de MFC, puede seguir utilizando estas macros en el código existente, mientras utiliza las excepciones de C\+\+ en el nuevo código.  El artículo [Excepciones: Cambios en las macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md) proporciona instrucciones para ello.  
  
> [!NOTE]
>  Para habilitar el control de excepciones de C\+\+ en el código, seleccione el permiso C\+\+ Excepciones en la generación de código en la carpeta C\/C\+\+ de cuadro de diálogo de [Páginas de propiedades](../ide/property-pages-visual-cpp.md) del proyecto, o utilice la opción del compilador \/GX.  El valor predeterminado es \/GX –, que deshabilita el control de excepciones.  
  
 En este artículo se tratan los siguientes temas:  
  
-   [Cuándo utilizar excepciones](#_core_when_to_use_exceptions)  
  
-   [Compatibilidad con la excepción de MFC](#_core_mfc_exception_support)  
  
-   [Información adicional sobre excepciones](#_core_further_reading_about_exceptions)  
  
##  <a name="_core_when_to_use_exceptions"></a> Cuándo utilizar Excepciones  
 Tres categorías de resultados pueden ocurrir cuando una función se llama durante la ejecución del programa: ejecución normal, ejecución de error, o ejecución anómala.  Cada categoría se describe a continuación.  
  
-   Ejecución normal  
  
     La función puede ejecutarse normalmente y volver.  Algunas funciones devuelven un código de resultado al llamador, que indica el resultado de la función.  Los códigos de resultado posibles se definen estrictamente para la función y representan el intervalo de los posibles resultados de la función.  El código de resultado puede indicar corrección o error o incluso puede indicar un tipo determinado de error que está comprendido en el intervalo normal de expectativas.  Por ejemplo, una función de estado de archivo puede devolver un código que indica que el archivo no existe.  Observe que el término “código de error” no se utiliza como un código de resultado representa uno de muchos resultados esperados.  
  
-   Ejecución errónea  
  
     El llamador incurre en alguna equivocación en pasar argumentos a la función o llama a la función en un contexto inadecuado.  Esta situación se produce un error, y debe ser detectado por una aserción durante el desarrollo de software. \(Para obtener más información sobre las aserciones, vea [Aserciones de C\/C\+\+](../Topic/C-C++%20Assertions.md).\)  
  
-   Ejecución anormal  
  
     La ejecución anormal incluye las situaciones en las condiciones fuera del control del programa, como memoria insuficiente o errores de E\/S, se influyen el resultado de la función.  Las situaciones anormales deben controlarse en la detección y excepciones.  
  
 Mediante excepciones es especialmente adecuado para la ejecución anómala.  
  
##  <a name="_core_mfc_exception_support"></a> Compatibilidad con la excepción de MFC  
 Si utiliza las excepciones de C\+\+ directamente o utiliza las macros de excepción de MFC, utilizará [CException Class](../mfc/reference/cexception-class.md) o `CException`\- objetos derivados que puede iniciar el marco o por la aplicación.  
  
 La tabla siguiente se muestran las excepciones predefinidas proporcionadas por MFC.  
  
|Clase de excepción|Significado|  
|------------------------|-----------------|  
|[CMemoryException Class](../mfc/reference/cmemoryexception-class.md)|En fuera\-de\- memoria|  
|[CFileException Class](../mfc/reference/cfileexception-class.md)|Excepción de archivo|  
|[CArchiveException Class](../mfc/reference/carchiveexception-class.md)|Excepción de archivos y de Serialización|  
|[CNotSupportedException Class](../mfc/reference/cnotsupportedexception-class.md)|Respuesta a la solicitud del servicio no compatibles|  
|[CResourceException Class](../mfc/reference/cresourceexception-class.md)|Excepción de la asignación de recursos de Windows|  
|[CDaoException Class](../mfc/reference/cdaoexception-class.md)|Excepciones de base de datos \(clases DAO\)|  
|[CDBException Class](../mfc/reference/cdbexception-class.md)|Excepciones de base de datos \(clases ODBC\)|  
|[COleException Class](../mfc/reference/coleexception-class.md)|Excepciones de OLE|  
|[COleDispatchException Class](../mfc/reference/coledispatchexception-class.md)|Excepciones de envío \(automatización\)|  
|[CUserException Class](../mfc/reference/cuserexception-class.md)|La excepción que avisa al usuario un cuadro de mensaje, inicia [CException Class](../mfc/reference/cexception-class.md)genérico|  
  
> [!NOTE]
>  MFC admite las excepciones de C\+\+ y macros de excepción de MFC.  MFC no admite directamente a los controladores de excepciones estructurados Windows NT \(SEH\), como se describe en [Control de excepciones estructurado](http://msdn.microsoft.com/library/windows/desktop/ms680657).  
  
##  <a name="_core_further_reading_about_exceptions"></a> Información adicional sobre excepciones  
 Los artículos siguientes explican mediante la biblioteca MFC para dar de excepción:  
  
-   [Excepciones: Detectar y eliminar excepciones](../mfc/exceptions-catching-and-deleting-exceptions.md)  
  
-   [Excepciones: Examinar contenidos de excepciones](../mfc/exceptions-examining-exception-contents.md)  
  
-   [Excepciones: Liberar objetos en las excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md)  
  
-   [Excepciones: Iniciar excepciones desde sus propias funciones](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md)  
  
-   [Excepciones: Excepciones de base de datos](../mfc/exceptions-database-exceptions.md)  
  
-   [Excepciones: Excepciones OLE](../mfc/exceptions-ole-exceptions.md)  
  
 Los artículos siguientes comparan las macros de excepción de MFC con las palabras clave de excepciones de C\+\+ y explica cómo puede adaptar el código:  
  
-   [Excepciones: Cambios en las macros de excepción en la versión 3.0](../mfc/exceptions-changes-to-exception-macros-in-version-3-0.md)  
  
-   [Excepciones: Convertir desde macros de excepciones de MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md)  
  
-   [Excepciones: Usar macros de MFC y excepciones de C\+\+](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md)  
  
## Vea también  
 [Control de excepciones de C\+\+](../cpp/cpp-exception-handling.md)   
 [Cómo se hago: ¿Cree mis clases de excepción personalizadas de Own?](http://go.microsoft.com/fwlink/?LinkId=128045)