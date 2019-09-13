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
ms.openlocfilehash: 983b3d9bc72d99ab3c665f86cffd205dccf873e8
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927899"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Compatibilidad con Unicode y con el juego de caracteres multibyte (MBCS)

Algunos idiomas, por ejemplo, el japonés y el chino, tienen juegos de caracteres de gran tamaño. Para admitir la programación de estos mercados, el biblioteca MFC (MFC) permite dos enfoques diferentes para administrar grandes conjuntos de caracteres:

- [Unicode](#mfc-support-for-unicode-strings), `wchar_t` caracteres anchos basados en y cadenas codificados como UTF-16.

- [Juegos de caracteres multibyte (MBCS)](#mfc-support-for-mbcs-strings) **, caracteres basados en caracteres** de un solo byte o de doble byte y cadenas codificadas en un juego de caracteres específico de la configuración regional.

Microsoft ha recomendado las bibliotecas de Unicode de MFC para todo el desarrollo nuevo y las bibliotecas de MBCS estaban en desuso en Visual Studio 2013 y Visual Studio 2015. Pero esto ya no es así. Las advertencias sobre desuso de MBCS se han quitado en Visual Studio 2017.

## <a name="mfc-support-for-unicode-strings"></a>Compatibilidad de MFC con cadenas Unicode

Toda la biblioteca de clases MFC se habilita condicionalmente para caracteres Unicode y cadenas almacenadas en caracteres anchos como UTF-16. En concreto, la clase [CString](../atl-mfc-shared/reference/cstringt-class.md) está habilitada para Unicode.

Estos archivos de biblioteca, depurador y DLL se usan para admitir Unicode en MFC:

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|*Versión*de MFC U. lib|*Versión*de MFC U. pdb|*Versión*de MFC U. dll|*Versión*de MFC Ud. OBJ|
|MFC*version*UD.PDB|*Versión*de MFC Ud. DLL|*Versión*de MFCS U. lib|*Versión*de MFCS U. pdb|
|MFCS*versión*Ud. OBJ|MFCS*version*UD.PDB|*Versión*de MFCM U. lib|*Versión*de MFCM U. pdb|
|MFCM*versión*U. dll|MFCM*versión*Ud. OBJ|MFCM*version*UD.PDB|MFCM*versión*Ud. DLL|

(la*versión* representa el número de versión del archivo; por ejemplo, ' 140 ' significa la versión 14,0).

`CString`se basa en el tipo de datos TCHAR. Si se define el símbolo _ Unicode para una compilación del programa, TCHAR se define como `wchar_t`tipo, un tipo de codificación de caracteres de 16 bits. De lo contrario, TCHAR se define como **Char**, la codificación de caracteres normal de 8 bits. Por consiguiente, en Unicode, `CString` consta de caracteres de 16 bits. Sin Unicode, se compone de caracteres de tipo **Char**.

Para completar la programación con Unicode de la aplicación, también debe hacer lo siguiente:

- Use la macro _ t para codificar condicionalmente cadenas literales para que sean portables a Unicode.

- Al pasar cadenas, observe con atención si los argumentos de función requieren una longitud en caracteres o una longitud en bytes. La diferencia es importante si utiliza cadenas Unicode.

- Utilice versiones portables de las funciones de control de cadenas en tiempo de ejecución de C.

- Utilice los tipos de datos siguientes para caracteres y punteros de caracteres:

   - Use TCHAR donde usaría **Char**.

   - Use LPTSTR donde usaría **Char**<strong>\*</strong>.

   - Use LPCTSTR, donde se usaría **const char**<strong>\*</strong>. `CString`proporciona el operador LPCTSTR para realizar la `CString` conversión entre y LPCTSTR.

`CString` también proporciona constructores, operadores de asignación y operadores de comparación que reconocen los caracteres Unicode.

La [referencia de la biblioteca en tiempo de ejecución](../c-runtime-library/c-run-time-library-reference.md) define las versiones portables de todas sus funciones de control de cadenas. Para obtener más información, consulte la categoría [internacionalización](../c-runtime-library/internationalization.md).

## <a name="mfc-support-for-mbcs-strings"></a>Compatibilidad de MFC con cadenas MBCS

La biblioteca de clases también está habilitada para los juegos de caracteres multibyte, pero solo para los juegos de caracteres de doble byte (DBCS).

En un juego de caracteres multibyte, un carácter puede ser de uno o dos bytes. Si es de dos bytes de ancho, el primer byte es un “byte inicial” que se elige de un intervalo determinado, según la página de códigos que esté en uso. Conjuntamente, los bytes iniciales y los “bytes finales” especifican una codificación de caracteres única.

Si se define el símbolo _ MBCS para una compilación del programa, el tipo TCHAR, en `CString` el que se basa, se asigna a **Char**. Decida si va a determinar qué bytes de `CString` son bytes iniciales y cuáles son bytes finales. La biblioteca en tiempo de ejecución de C proporciona funciones para ayudarle a determinarlo.

En DBCS, una cadena determinada puede contener solo caracteres ANSI de byte único, solo caracteres de doble byte o una combinación de ambos. Estas posibilidades requieren un cuidado especial al analizar las cadenas. Esto incluye los objetos `CString`.

> [!NOTE]
> La serialización de cadenas Unicode en MFC puede leer cadenas Unicode y MBCS sin tener en cuenta qué versión de la aplicación se está ejecutando. Los archivos de datos son portables entre las versiones Unicode y MBCS del programa.

Las funciones miembro de `CString` utilizan versiones de “texto genérico” especiales de las funciones en tiempo de ejecución de C a las que llaman o usan funciones que reconocen Unicode. En consecuencia, si, por ejemplo, una función `CString` llamaría normalmente a `strcmp`, llama a la función de texto genérico `_tcscmp` correspondiente en su lugar. En función de cómo se hayan definido los símbolos _ MBCS y `_tcscmp` _ Unicode, se asigna de la siguiente manera:

|||
|-|-|
|_MBCS definido|`_mbscmp`|
|_UNICODE definido|`wcscmp`|
|Ninguno de los dos símbolos definidos|`strcmp`|

> [!NOTE]
> Los símbolos _ MBCS y _ Unicode son mutuamente excluyentes.

Las asignaciones de funciones de texto genérico para todas las rutinas de control de cadenas en tiempo de ejecución se describen en [referencia de la biblioteca en tiempo de ejecución de C](../c-runtime-library/c-run-time-library-reference.md). Para obtener una lista, vea [internacionalización](../c-runtime-library/internationalization.md).

Del mismo `CString` modo, los métodos se implementan mediante asignaciones de tipos de datos genéricos. Para habilitar MBCS y Unicode, MFC usa TCHAR para **Char** o `wchar_t`, LPTSTR para **Char** <strong>\*</strong> o `wchar_t*`, y LPCTSTR para **const char** <strong>\*</strong> o. `const wchar_t*` Esto garantiza las asignaciones correctas para MBCS o Unicode.

## <a name="see-also"></a>Vea también

[Cadenas (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[Manipulación de cadenas](../c-runtime-library/string-manipulation-crt.md)
