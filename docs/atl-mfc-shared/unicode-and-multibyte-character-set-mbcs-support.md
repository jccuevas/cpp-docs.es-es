---
title: Unicode y juegos de caracteres Multibyte (MBCS) soporte de establecer | Microsoft Docs
ms.custom: ''
ms.date: 1/09/2017
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e9d212e74f77d21efa1b2ed030f8a1446d111fc
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882954"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)

Algunos idiomas, por ejemplo, el japonés y el chino, tienen juegos de caracteres de gran tamaño. Para admitir la programación para estos mercados, la biblioteca de clases (MFC) de Microsoft Foundation permite dos enfoques diferentes para controlar conjuntos de caracteres de gran tamaño:

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` en función de caracteres anchos y cadenas codificadas como UTF-16.

- [Conjuntos de caracteres multibyte (MBCS)](#mfc-support-for-mbcs-strings), **char** basado únicos o de doble byte caracteres y cadenas con codificación en un juego de caracteres de la configuración regional específica.

Microsoft recomienda las bibliotecas MFC Unicode para todo el desarrollo nuevo, y las bibliotecas de MBCS han quedado en desuso en Visual Studio 2013 y Visual Studio 2015. Pero esto ya no es así. Se han quitado las advertencias sobre desuso de MBCS en Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Compatibilidad de MFC con cadenas Unicode

Toda la biblioteca de clases MFC se habilita condicionalmente para los caracteres Unicode y las cadenas almacenadas en caracteres anchos como UTF-16. En concreto, la clase [CString](../atl-mfc-shared/reference/cstringt-class.md) está habilitada para Unicode.

Estos archivos DLL, el depurador y la biblioteca se utilizan para admitir Unicode en MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|MFC*versión*U.LIB|MFC*versión*U.PDB|MFC*versión*U.DLL|MFC*versión*UD. LIB|
|MFC*versión*UD. PDB|MFC*versión*UD. ARCHIVO DLL|MFCS*versión*U.LIB|MFCS*versión*U.PDB|
|MFCS*versión*UD. LIB|MFCS*versión*UD. PDB|MFCM*versión*U.LIB|MFCM*versión*U.PDB|
|MFCM*versión*U.DLL|MFCM*versión*UD. LIB|MFCM*versión*UD. PDB|MFCM*versión*UD. ARCHIVO DLL|

(*versión* representa el número de versión del archivo; por ejemplo, "140" significa versión 14.0.)

`CString` se basa en el tipo de datos TCHAR. Si se define el símbolo _UNICODE para una compilación del programa, TCHAR se define como tipo `wchar_t`, un tipo de codificación de carácter de 16 bits. En caso contrario, se considera TCHAR **char**, la codificación de caracteres de 8 bits normal. Por consiguiente, en Unicode, `CString` consta de caracteres de 16 bits. Sin Unicode, se compone de caracteres de tipo **char**.

Para completar la programación con Unicode de la aplicación, también debe hacer lo siguiente:

- Utilice la macro _T condicionalmente código las cadenas literales que sean portables a Unicode.

- Al pasar cadenas, observe con atención si los argumentos de función requieren una longitud en caracteres o una longitud en bytes. La diferencia es importante si utiliza cadenas Unicode.

- Utilice versiones portables de las funciones de control de cadenas en tiempo de ejecución de C.

- Utilice los tipos de datos siguientes para caracteres y punteros de caracteres:

   - Usar TCHAR donde utilizaría **char**.

   - Usar LPTSTR donde utilizaría **char\***.

   - Usar LPCTSTR donde utilizaría **const char\***. `CString` proporciona el operador LPCTSTR para convertir entre `CString` y LPCTSTR.

`CString` también proporciona constructores, operadores de asignación y operadores de comparación que reconocen los caracteres Unicode.

El [referencia de la biblioteca de tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) define las versiones portables de todas sus funciones de control de cadenas. Para obtener más información, vea la categoría [internacionalización](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Compatibilidad de MFC con cadenas MBCS

La biblioteca de clases también está habilitada para los juegos de caracteres multibyte, pero solo para los juegos de caracteres de doble byte (DBCS).

En un juego de caracteres multibyte, un carácter puede ser de uno o dos bytes. Si es de dos bytes de ancho, el primer byte es un “byte inicial” que se elige de un intervalo determinado, según la página de códigos que esté en uso. Conjuntamente, los bytes iniciales y los “bytes finales” especifican una codificación de caracteres única.

Si el símbolo _MBCS definido para una compilación del programa, escriba TCHAR, en el que `CString` se basa, se asigna a **char**. Decida si va a determinar qué bytes de `CString` son bytes iniciales y cuáles son bytes finales. La biblioteca en tiempo de ejecución de C proporciona funciones para ayudarle a determinarlo.

En DBCS, una cadena determinada puede contener solo caracteres ANSI de byte único, solo caracteres de doble byte o una combinación de ambos. Estas posibilidades requieren un cuidado especial al analizar las cadenas. Esto incluye los objetos `CString`.

> [!NOTE]
> La serialización de cadenas Unicode en MFC puede leer cadenas Unicode y MBCS sin tener en cuenta qué versión de la aplicación se está ejecutando. Los archivos de datos son portables entre las versiones Unicode y MBCS del programa.

Las funciones miembro de `CString` utilizan versiones de “texto genérico” especiales de las funciones en tiempo de ejecución de C a las que llaman o usan funciones que reconocen Unicode. En consecuencia, si, por ejemplo, una función `CString` llamaría normalmente a `strcmp`, llama a la función de texto genérico `_tcscmp` correspondiente en su lugar. Dependiendo de cómo se definen los símbolos _MBCS y _UNICODE, `_tcscmp` asigna como sigue:

|||
|-|-|
|_MBCS definido|`_mbscmp`|
|_UNICODE definido|`wcscmp`|
|Ninguno de los dos símbolos definidos|`strcmp`|

> [!NOTE]
> Los símbolos _MBCS y _UNICODE son mutuamente excluyentes.

Asignaciones de función de texto genérico para todas las rutinas de control de cadenas de tiempo de ejecución se tratan en [C Run-Time Library Reference](../c-runtime-library/c-run-time-library-reference.md). Para obtener una lista, consulte [internacionalización](../c-runtime-library/internationalization.md).

De forma similar, `CString` métodos se implementan mediante asignaciones de tipos de datos genéricos. Para habilitar MBCS y Unicode, MFC utiliza TCHAR para **char** o `wchar_t`, LPTSTR para **char\***  o `wchar_t*`y LPCTSTR para **const char\***  o `const wchar_t*`. Esto garantiza las asignaciones correctas para MBCS o Unicode.

## <a name="see-also"></a>Vea también

[Cadenas (ATL y MFC)](../atl-mfc-shared/strings-atl-mfc.md)  
[Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md)  
