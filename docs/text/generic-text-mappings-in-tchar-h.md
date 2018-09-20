---
title: Asignaciones de texto genérico en Tchar.h | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- tchar.h
dev_langs:
- C++
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5959e026df9fcffc3295000b3d433aab16100fb6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375310"
---
# <a name="generic-text-mappings-in-tcharh"></a>Asignaciones de texto genérico en TCHAR.H

Para simplificar la conversión de código para uso internacional, la biblioteca de tiempo de ejecución de Microsoft proporciona asignaciones de texto genérico específicas de Microsoft para muchos tipos de datos, rutinas y otros objetos. Puede usar estas asignaciones, que se definen en Tchar.h, para escribir código genérico que se puede compilar para un solo byte, multibyte, o juegos de caracteres de Unicode, dependiendo de una constante de manifiesto que define mediante un `#define` instrucción. Las asignaciones de texto genérico son extensiones de Microsoft que no son compatibles con ANSI.

Utilizando el archivo Tchar.h, puede compilar aplicaciones de Unicode de las mismas fuentes, juego de caracteres Multibyte (MBCS) y un byte. Tchar.h define macros (que tienen el prefijo `_tcs`) que, con las definiciones de preprocesador correctas, se asignan a las funciones `str`, `_mbs` o `wcs`, según proceda. Para compilar MBCS, se ha de definir el símbolo `_MBCS`. Para compilar Unicode, definir el símbolo `_UNICODE`. Para compilar una aplicación de un solo byte, no hay que definir ningún símbolo (opción predeterminada). De forma predeterminada, `_MBCS` está definido para aplicaciones MFC.

El tipo de datos `_TCHAR` se define de forma condicional en Tchar.h. Si el símbolo `_UNICODE` se define para la compilación, `_TCHAR` se define como **wchar_t**; en caso contrario, para compilaciones MBCS y de un solo byte, se define como **char**. (**wchar_t**, el tipo de datos de caracteres anchos Unicode básico es el equivalente de 16 bits a un 8 bits con signo **char**.) Para aplicaciones internacionales, se ha de utilizar la familia de funciones `_tcs`, que se ejecuta en unidades `_TCHAR`, no en bytes. Por ejemplo, `_tcsncpy` copias `n` `_TCHARs`, no `n` bytes.

Dado que algunas funciones de control de cadenas de juego de caracteres de byte único (SBCS) reciben parámetros `char*` (con signo), se genera una advertencia del compilador indicando que el tipo no coincide cuando se define `_MBCS`. Hay tres formas de evitar esta advertencia:

1. Use fragmentos de código thunk de función inline con seguridad de tipos en Tchar.h. Éste es el comportamiento predeterminado.

1. Use las macros directas en Tchar.h definiendo `_MB_MAP_DIRECT` en la línea de comandos. Si lo hace, deberá hacer coincidir los tipos manualmente. Este es el método más rápido, pero no garantiza la seguridad de tipos.

1. Use fragmentos de código thunk de función de biblioteca vinculada estáticamente con seguridad de tipos en Tchar.h. Para ello, defina la constante `_NO_INLINING` en la línea de comandos. Este es el método más lento, pero garantiza prácticamente la seguridad de tipos.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directivas de preprocesador para asignaciones de texto genérico

|# define|Versión compilada|Ejemplo|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (carácter ancho)|`_tcsrev` se asigna a `_wcsrev`|
|`_MBCS`|Carácter multibyte|`_tcsrev` se asigna a `_mbsrev`|
|Ninguno (la opción predeterminada no tiene definidos `_UNICODE` ni `_MBCS`)|SBCS (ASCII)|`_tcsrev` se asigna a `strrev`|

Por ejemplo, la función de texto genérico `_tcsrev`, definida en Tchar.h, se asigna a `_mbsrev` si se ha definido `_MBCS` en el programa, o a `_wcsrev` si se ha definido `_UNICODE`. De lo contrario, `_tcsrev` se asigna a `strrev`. Las asignaciones de otros tipos de datos se proporcionan en Tchar.h para mayor comodidad en la programación, pero `_TCHAR` es la más útil.

### <a name="generic-text-data-type-mappings"></a>Asignaciones de tipos de datos de texto genérico

|Texto genérico <br /> Nombre de tipo de datos|_UNICODE y<br /> _MBCS no definidos|_MBCS<br /> Definido|_UNICODE<br /> Definido|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**carácter con signo**|**carácter con signo**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` o `_TEXT`|Sin efecto (quitado por el preprocesador)|Sin efecto (quitado por el preprocesador)|`L` (convierte el carácter o cadena siguiente en su equivalente de Unicode)|

Para obtener una lista de asignaciones de texto genérico de rutinas, variables y otros objetos, consulte [asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en la referencia de la biblioteca de tiempo de ejecución.

> [!NOTE]
>  No utilice la familia `str` de funciones con cadenas de Unicode, ya que probablemente contendrán bytes nulos incrustados. Del mismo modo, no use la familia de funciones `wcs` con cadenas MBCS (o SBCS).

Los siguientes fragmentos de código muestran el uso de `_TCHAR` y `_tcsrev` para la asignación a los modelos MBCS, Unicode y SBCS.

```cpp
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Si se ha definido `_MBCS`, el preprocesador asigna este fragmento a este código:

```cpp
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Si se ha definido `_UNICODE`, el preprocesador asigna este fragmento a este código:

```cpp
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Si no `_MBCS` ni `_UNICODE` han sido definido, el preprocesador asigna el fragmento a código ASCII de byte único, como se indica a continuación:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Por lo tanto, se puede crear, mantener y compilar un único archivo de código fuente para su ejecución con rutinas específicas de cualquiera de los tres tipos de juegos de caracteres.

## <a name="see-also"></a>Vea también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)<br/>
[Uso de tipos de datos de TCHAR.H con código _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)