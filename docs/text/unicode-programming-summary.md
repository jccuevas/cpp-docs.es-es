---
title: Resumen de la programación de Unicode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 78e40e258334ed1e9622e31e8452810f231cb61f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42582008"
---
# <a name="unicode-programming-summary"></a>Resumen de la programación con Unicode
Para disfrutar de las ventajas de la compatibilidad en tiempo de ejecución de C y MFC con Unicode, es necesario:  
  
-   Definir `_UNICODE`.  
  
     Definir el símbolo `_UNICODE` antes de compilar el programa.  
  
-   Especificar el punto de entrada.  
  
     En el **salida** página de la **vinculador** carpeta del proyecto [páginas de propiedades](../ide/property-pages-visual-cpp.md) cuadro de diálogo, establezca el **punto de entrada** símbolos para `wWinMainCRTStartup`.  
  
-   Utilizar tipos y funciones portables en tiempo de ejecución.  
  
     Para el control de cadenas de Unicode se han de utilizar las funciones en tiempo de ejecución de C adecuadas. Puede usar el `wcs` familia de funciones, pero es posible que prefiera totalmente portables (habilitadas internacionalmente) `_TCHAR` macros. Todas estas macros tienen el prefijo con `_tcs`; sustituyen, uno a uno, para el `str` familia de funciones. Estas funciones se describen en detalle en la [internacionalización](../c-runtime-library/internationalization.md) sección de la *referencia de la biblioteca de tiempo de ejecución*. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Use `_TCHAR` y los tipos de datos portables relacionados que se describe en [compatibilidad con Unicode](../text/support-for-unicode.md).  
  
-   Controlar las cadenas literales de forma adecuada.  
  
     El compilador de Visual C++ interpreta una cadena literal codificada como:  
  
    ```  
    L"this is a literal string"  
    ```  
  
     para indicar una cadena de caracteres Unicode. Se puede utilizar el mismo prefijo para los literales de cadena. Use el `_T` macro para codificar cadenas literales de forma genérica, para que se compilen como cadenas de Unicode bajo Unicode o como cadenas ANSI (incluyendo MBCS) sin Unicode. Por ejemplo, en lugar de:  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     utilice:  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     Con `_UNICODE` definido, `_T` convierte la cadena literal en la forma con L inicial; de lo contrario, `_T` convierte la cadena sin el prefijo L.  
  
    > [!TIP]
    >  El `_T` macro es idéntica a la `_TEXT` macro.  
  
-   Adoptar precauciones al pasar longitudes de cadenas a funciones.  
  
     Algunas funciones requieren el número de caracteres de una cadena; otras requieren el número de bytes. Por ejemplo, si `_UNICODE` está definido, la llamada siguiente a un `CArchive` objeto no funcionará (`str` es un `CString`):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     En una aplicación de Unicode, la longitud proporciona el número de caracteres pero no el número correcto de bytes, ya que cada carácter tiene un ancho de 2 bytes. En su lugar, se debe utilizar:  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     que especifica el número correcto de bytes que se han de escribir.  
  
     Sin embargo, las funciones miembro de MFC que están orientadas a caracteres, en lugar de estar orientadas a bytes, funcionan sin este código adicional:  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` recibe un número de caracteres, no un número de bytes.  
  
-   Use [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) para abrir los archivos Unicode.  
  
 En resumen, MFC y la biblioteca en tiempo de ejecución proporcionan la siguiente compatibilidad para la programación de Unicode:  
  
-   Excepto para las funciones miembro de clase de base de datos, todas las funciones MFC están habilitadas para Unicode, incluso `CString`. `CString` también proporciona funciones de conversión Unicode/ANSI.  
  
-   La biblioteca en tiempo de ejecución proporciona versiones de Unicode de todas las funciones de control de cadenas. La biblioteca en tiempo de ejecución también proporciona versiones portables apropiadas tanto para Unicode como para MBCS. Estos son los `_tcs` macros.)  
  
-   Tchar.h proporciona tipos de datos portables y la `_T` macro para convertir cadenas literales y caracteres. Para obtener más información, consulte [asignaciones de texto genérico en Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   La biblioteca en tiempo de ejecución proporciona una versión con caracteres anchos de `main`. Use `wmain` para hacer que su aplicación compatible con Unicode.  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con Unicode](../text/support-for-unicode.md)