---
title: "Resumen de la programaci&#243;n con Unicode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unicode [C++], funciones en tiempo de ejecución de MFC y C"
  - "Unicode [C++], programar"
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
caps.latest.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 8
---
# Resumen de la programaci&#243;n con Unicode
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para disfrutar de las ventajas de la compatibilidad en tiempo de ejecución de C y MFC con Unicode, es necesario:  
  
-   Definir **\_UNICODE**.  
  
     Definir el símbolo **\_UNICODE** antes de compilar el programa.  
  
-   Especificar el punto de entrada.  
  
     En la página **Avanzado** de la carpeta Vinculador del cuadro de diálogo [Páginas de propiedades](../ide/property-pages-visual-cpp.md) del proyecto, establecer el símbolo del punto de entrada en **wWinMainCRTStartup**.  
  
-   Utilizar tipos y funciones portables en tiempo de ejecución.  
  
     Para el control de cadenas de Unicode se han de utilizar las funciones en tiempo de ejecución de C adecuadas.  Se puede utilizar la familia de funciones **wcs**, pero puede ser preferible utilizar las macros **\_TCHAR** totalmente portables \(habilitadas internacionalmente\).  Todas estas macros tienen el prefijo **\_tcs**; sustituyen, de una en una, a la familia de funciones **str**.  Estas funciones se describen detalladamente en la sección [Internacionalización](../c-runtime-library/internationalization.md) de la *Referencia de la biblioteca en tiempo de ejecución.* Para obtener más información, vea [Asignaciones de texto genérico en Tchar.h](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md).  
  
     Utilice **\_TCHAR** y los tipos de datos portables relacionados que se describen en [Compatibilidad con Unicode](../text/support-for-unicode.md).  
  
-   Controlar las cadenas literales de forma adecuada.  
  
     El compilador de Visual C\+\+ interpreta una cadena literal codificada como:  
  
    ```  
    L"this is a literal string"  
    ```  
  
     para indicar una cadena de caracteres Unicode.  Se puede utilizar el mismo prefijo para los literales de cadena.  Utilice la macro **\_T** para codificar cadenas literales de forma genérica, para que se compilen como cadenas de Unicode bajo Unicode o como cadenas ANSI \(incluyendo MBCS\) sin Unicode.  Por ejemplo, en lugar de:  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     utilice:  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     Con el símbolo **\_UNICODE** definido, **\_T** convierte la cadena literal en la forma con L inicial; de lo contrario, **\_T** convierte la cadena sin la L inicial.  
  
    > [!TIP]
    >  El comportamiento de la macro **\_T** es idéntico al de la macro `_TEXT`.  
  
-   Adoptar precauciones al pasar longitudes de cadenas a funciones.  
  
     Algunas funciones requieren el número de caracteres de una cadena; otras requieren el número de bytes.  Por ejemplo, si el símbolo **\_UNICODE** está definido, la llamada siguiente a un objeto `CArchive` no funcionará \(`str` es una clase `CString`\):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     En una aplicación de Unicode, la longitud proporciona el número de caracteres pero no el número correcto de bytes, ya que cada carácter tiene un ancho de 2 bytes.  En su lugar, se debe utilizar:  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     que especifica el número correcto de bytes que se han de escribir.  
  
     Sin embargo, las funciones miembro de MFC que están orientadas a caracteres, en lugar de estar orientadas a bytes, funcionan sin este código adicional:  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` recibe un número de caracteres, no un número de bytes.  
  
-   Utilice [fopen\_s, \_wfopen\_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) para abrir los archivos Unicode.  
  
 En resumen, MFC y la biblioteca en tiempo en ejecución proporcionan la siguiente compatibilidad para la programación con Unicode bajo Windows 2000:  
  
-   Excepto para las funciones miembro de clase de base de datos, todas las funciones MFC están habilitadas para Unicode, incluso `CString`.  `CString` también proporciona funciones de conversión Unicode\/ANSI.  
  
-   La biblioteca en tiempo de ejecución proporciona versiones de Unicode de todas las funciones de control de cadenas. La biblioteca en tiempo de ejecución también proporciona versiones portables apropiadas tanto para Unicode como para MBCS.  Son las macros **\_tcs**.  
  
-   Tchar.h proporciona tipos de datos portables y la macro **\_T** para convertir cadenas literales y caracteres.  Para obtener más información, vea [Asignaciones de texto genérico en Tchar.h](../Topic/Generic-Text%20Mappings%20in%20Tchar.h.md).  
  
-   La biblioteca en tiempo de ejecución proporciona una versión con caracteres anchos de **main**.  Utilice **wmain** para que la aplicación esté preparada para Unicode.  
  
## Vea también  
 [Compatibilidad con Unicode](../text/support-for-unicode.md)