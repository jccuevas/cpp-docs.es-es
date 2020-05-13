---
title: Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: e1b93a3540cba553afd8f133c18496bddbd561b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317436"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)

Algunos idiomas, por ejemplo, el japonés y el chino, tienen juegos de caracteres de gran tamaño. Para admitir la programación para estos mercados, la biblioteca Microsoft Foundation Class (MFC) habilita dos enfoques diferentes para controlar grandes conjuntos de caracteres:

- [Unicode](#mfc-support-for-unicode-strings) `wchar_t` , basado en caracteres anchos y cadenas codificadas como UTF-16.

- [Conjuntos de caracteres multibyte (MBCS),](#mfc-support-for-mbcs-strings)caracteres basados en **caracteres** de uno o dos bytes y cadenas codificadas en un juego de caracteres específico de la configuración regional.

Microsoft ha recomendado las bibliotecas Unicode de MFC para todo el nuevo desarrollo y las bibliotecas MBCS estaban en desuso en Visual Studio 2013 y Visual Studio 2015. Este ya no es el caso. Las advertencias de desuso de MBCS se han quitado en Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Compatibilidad de MFC con cadenas Unicode

Toda la biblioteca de clases MFC está habilitada condicionalmente para caracteres Unicode y cadenas almacenadas en caracteres anchos como UTF-16. En particular, la clase [CString](../atl-mfc-shared/reference/cstringt-class.md) está habilitada para Unicode.

Estos archivos de biblioteca, depurador y DLL se utilizan para admitir Unicode en MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|*Versión*MFC U.LIB|*Versión*MFC U.PDB|*Versión*de MFC U.DLL|*Versión*de MFC UD. Lib|
|*Versión*de MFC UD. Pdb|*Versión*de MFC UD. Dll|Versión u.LIB*de*MFCS|Versión U.PDB*de*MFCS|
|*VERSIÓn*DE MFCS UD. Lib|*VERSIÓn*DE MFCS UD. Pdb|Versión*version*MFCM U.LIB|Versión*version*MFCM U.PDB|
|Versión U.DLL*de*MFCM|*Versión*de MFCM UD. Lib|*Versión*de MFCM UD. Pdb|*Versión*de MFCM UD. Dll|

(*versión* representa el número de versión del archivo; por ejemplo, '140' significa versión 14.0.)

`CString`se basa en el tipo de datos TCHAR. Si el símbolo _UNICODE se define para una compilación del `wchar_t`programa, TCHAR se define como tipo, un tipo de codificación de caracteres de 16 bits. De lo contrario, TCHAR se define como **char**, la codificación de caracteres normal de 8 bits. Por consiguiente, en Unicode, `CString` consta de caracteres de 16 bits. Sin Unicode, se compone de caracteres de tipo **char**.

Para completar la programación con Unicode de la aplicación, también debe hacer lo siguiente:

- Utilice la macro _T para codificar condicionalmente cadenas literales para que sean portables a Unicode.

- Al pasar cadenas, observe con atención si los argumentos de función requieren una longitud en caracteres o una longitud en bytes. La diferencia es importante si utiliza cadenas Unicode.

- Utilice versiones portables de las funciones de control de cadenas en tiempo de ejecución de C.

- Utilice los tipos de datos siguientes para caracteres y punteros de caracteres:

  - Utilice TCHAR donde usaría **char**.

  - Utilice LPTSTR donde usaría **char**<strong>\*</strong>.

  - Utilice LPCTSTR donde usaría **const char**<strong>\*</strong>. `CString`proporciona al operador LPCTSTR `CString` para convertir entre y LPCTSTR.

`CString` también proporciona constructores, operadores de asignación y operadores de comparación que reconocen los caracteres Unicode.

La referencia de la [biblioteca en tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) define las versiones portátiles de todas sus funciones de control de cadenas. Para obtener más información, consulte la categoría [Internacionalización](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Compatibilidad de MFC con cadenas MBCS

La biblioteca de clases también está habilitada para los juegos de caracteres multibyte, pero solo para los juegos de caracteres de doble byte (DBCS).

En un juego de caracteres multibyte, un carácter puede ser de uno o dos bytes. Si es de dos bytes de ancho, el primer byte es un “byte inicial” que se elige de un intervalo determinado, según la página de códigos que esté en uso. Conjuntamente, los bytes iniciales y los “bytes finales” especifican una codificación de caracteres única.

Si el símbolo _MBCS se define para una compilación del `CString` programa, escriba TCHAR, en el que se basa, se asigna a **char**. Decida si va a determinar qué bytes de `CString` son bytes iniciales y cuáles son bytes finales. La biblioteca en tiempo de ejecución de C proporciona funciones para ayudarle a determinarlo.

En DBCS, una cadena determinada puede contener solo caracteres ANSI de byte único, solo caracteres de doble byte o una combinación de ambos. Estas posibilidades requieren un cuidado especial al analizar las cadenas. Esto incluye los objetos `CString`.

> [!NOTE]
> La serialización de cadenas Unicode en MFC puede leer cadenas Unicode y MBCS sin tener en cuenta qué versión de la aplicación se está ejecutando. Los archivos de datos son portables entre las versiones Unicode y MBCS del programa.

Las funciones miembro de `CString` utilizan versiones de “texto genérico” especiales de las funciones en tiempo de ejecución de C a las que llaman o usan funciones que reconocen Unicode. En consecuencia, si, por ejemplo, una función `CString` llamaría normalmente a `strcmp`, llama a la función de texto genérico `_tcscmp` correspondiente en su lugar. Dependiendo de cómo se definan `_tcscmp` los símbolos _MBCS y _UNICODE, se asignan de la siguiente manera:

|||
|-|-|
|_MBCS definido|`_mbscmp`|
|_UNICODE definido|`wcscmp`|
|Ninguno de los dos símbolos definidos|`strcmp`|

> [!NOTE]
> Los símbolos _MBCS y _UNICODE son mutuamente excluyentes.

Las asignaciones de funciones de texto genérico para todas las rutinas de control de cadenas en tiempo de ejecución se describen en [Referencia de](../c-runtime-library/c-run-time-library-reference.md)biblioteca en tiempo de ejecución de C . Para obtener una lista, consulte [Internacionalización](../c-runtime-library/internationalization.md).

De `CString` forma similar, los métodos se implementan mediante asignaciones de tipos de datos genéricos. Para habilitar MBCS y Unicode, MFC utiliza `wchar_t`TCHAR para **char** `wchar_t*`o , LPTSTR para **char** <strong>\*</strong> o , y LPCTSTR para **const char** <strong>\*</strong> o `const wchar_t*`. Esto garantiza las asignaciones correctas para MBCS o Unicode.

## <a name="see-also"></a>Consulte también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulación de cuerdas](../c-runtime-library/string-manipulation-crt.md)
