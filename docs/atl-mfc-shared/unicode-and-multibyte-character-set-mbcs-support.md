---
title: "Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MFC [C++], compatibilidad con juego de caracteres"
  - "MBCS [C++], compatibilidad con cadenas y MFC"
  - "cadenas [C++], compatibilidad con MBCS en MFC"
  - "juegos de caracteres [C++], multibyte"
  - "Unicode [C++], cadenas de MFC"
  - "Unicode [C++], objetos de cadena"
  - "cadenas [C++], Unicode"
  - "cadenas [C++], compatibilidad con juego de caracteres"
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Algunos idiomas, por ejemplo, el japonés y el chino, tienen juegos de caracteres de gran tamaño.  Para permitir la programación en estos mercados, la biblioteca MFC \(Microsoft Foundation Class\) está habilitada para dos enfoques diferentes de la administración de juegos de caracteres de gran tamaño:  
  
-   [Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [Juegos de caracteres multibyte \(MBCS\)](#_core_mfc_support_for_mbcs_strings)  
  
 Debe utilizar Unicode para todo el desarrollo nuevo.  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a> Compatibilidad de MFC con cadenas Unicode  
 La biblioteca de clases completa se habilita condicionalmente para los caracteres y cadenas Unicode.  En particular, la clase [CString](../atl-mfc-shared/reference/cstringt-class.md) está habilitada para Unicode.  
  
|||||  
|-|-|-|-|  
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD.LIB|  
|MFC*xx*UD.PDB|MFC*xx*UD.DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD.LIB|MFCS*xx*UD.PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD.LIB|MFCM*xx*UD.PDB|MFCM*xx*UD.DLL|  
  
 \(*xx* representa el número de versión del archivo; por ejemplo, “80" significa versión 8.0\).  
  
 `CString` se basa en el tipo de datos `TCHAR`.  Si el símbolo `_UNICODE` se define para una compilación del programa, `TCHAR` se define como `wchar_t`, que es un tipo de codificación de caracteres de 16 bits.  De lo contrario, `TCHAR` se define como `char`, que es la codificación de caracteres de 8 bits normal.  Por consiguiente, en Unicode, `CString` consta de caracteres de 16 bits.  Sin Unicode, consta de caracteres de tipo `char`.  
  
 Para completar la programación con Unicode de la aplicación, también debe hacer lo siguiente:  
  
-   Utilice la macro `_T` para codificar condicionalmente las cadenas literales de código de forma que sean portables a Unicode.  
  
-   Al pasar cadenas, observe con atención si los argumentos de función requieren una longitud en caracteres o una longitud en bytes.  La diferencia es importante si utiliza cadenas Unicode.  
  
-   Utilice versiones portables de las funciones de control de cadenas en tiempo de ejecución de C.  
  
-   Utilice los tipos de datos siguientes para caracteres y punteros de caracteres:  
  
    -   `TCHAR` Donde utilizaría `char`.  
  
    -   `LPTSTR` Donde utilizaría `char*`.  
  
    -   `LPCTSTR` Donde utilizaría `const char*`.  `CString` proporciona el operador `LPCTSTR` para convertir entre `CString` y `LPCTSTR`.  
  
 `CString` también proporciona constructores, operadores de asignación y operadores de comparación que reconocen los caracteres Unicode.  
  
 Para obtener información relacionada sobre la programación con Unicode, vea [Temas de Unicode](../mfc/unicode-in-mfc.md).  La [Referencia de la biblioteca en tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) define las versiones portables de todas sus funciones de control de cadenas.  Vea la categoría [Internacionalización](../c-runtime-library/internationalization.md).  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a> Compatibilidad de MFC con cadenas MBCS  
  
> [!WARNING]
>  Las cadenas MBCS son tecnología heredada y no deben usarse en proyectos nuevos.  La siguiente información se proporciona para escenarios en los que es necesario mantener el código existente que utiliza MBCS y no es posible actualizar el código para utilizar Unicode.  
  
 La biblioteca de clases también está habilitada para los juegos de caracteres multibyte, pero solo para los juegos de caracteres de doble byte \(DBCS\).  
  
> [!IMPORTANT]
>  En [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] y versiones posteriores, las versiones MBCS de los archivos DLL de MFC están disponibles como complemento gratuito para Visual Studio en el sitio de descarga de MSDN.  Para obtener más información, vea [Complemento DLL de MBCS para MFC](../mfc/mfc-mbcs-dll-add-on.md).  
  
 En un juego de caracteres multibyte, un carácter puede ser de uno o dos bytes.  Si es de dos bytes de ancho, el primer byte es un “byte inicial” que se elige de un intervalo determinado, según la página de códigos que esté en uso.  Conjuntamente, los bytes iniciales y los “bytes finales” especifican una codificación de caracteres única.  
  
 Si se define el símbolo `_MBCS` para una compilación del programa, el tipo `TCHAR` en el que se basa `CString` se asigna a `char`.  Decida si va a determinar qué bytes de `CString` son bytes iniciales y cuáles son bytes finales.  La biblioteca en tiempo de ejecución de C proporciona funciones para ayudarle a determinarlo.  
  
 En DBCS, una cadena determinada puede contener solo caracteres ANSI de byte único, solo caracteres de doble byte o una combinación de ambos.  Estas posibilidades requieren un cuidado especial al analizar las cadenas.  Esto incluye los objetos `CString`.  
  
> [!NOTE]
>  La serialización de cadenas Unicode en MFC puede leer cadenas Unicode y MBCS sin tener en cuenta qué versión de la aplicación se está ejecutando.  Los archivos de datos son portables entre las versiones Unicode y MBCS del programa.  
  
 Las funciones miembro de `CString` utilizan versiones de “texto genérico” especiales de las funciones en tiempo de ejecución de C a las que llaman o usan funciones que reconocen Unicode.  En consecuencia, si, por ejemplo, una función `CString` llamaría normalmente a `strcmp`, llama a la función de texto genérico `_tcscmp` correspondiente en su lugar.  Según la forma en que se hayan definido los símbolos `_MBCS` y `_UNICODE`, `_tcscmp` se asigna como sigue:  
  
|||  
|-|-|  
|`_MBCS` definido|`_mbscmp`|  
|`_UNICODE` definido|`wcscmp`|  
|Ninguno de los dos símbolos definidos|`strcmp`|  
  
> [!NOTE]
>  Los símbolos `_MBCS` y `_UNICODE` se excluyen mutuamente.  
  
 Las asignaciones de funciones de texto genérico para todas las rutinas de control de cadenas en tiempo de ejecución se tratan en [Referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md).  En concreto, vea [Internacionalización](../c-runtime-library/internationalization.md).  
  
 De igual forma, los métodos de `CString` se implementan mediante asignaciones de tipo de datos “genéricas”.  Para habilitar MBCS y Unicode, MFC utiliza `TCHAR` para `char`, `LPTSTR` para `char*` y `LPCTSTR` para `const char*`.  Esto garantiza las asignaciones correctas para MBCS o Unicode.  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md)