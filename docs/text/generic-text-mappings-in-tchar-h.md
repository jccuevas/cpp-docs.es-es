---
title: Asignaciones de texto genérico en tchar.h
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text mappings [C++]
- character sets [C++], generic-text mappings
- Unicode [C++], generic-text mappings
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 01e1bb74-5a01-4093-8720-68b6c1fdda80
ms.openlocfilehash: bf872df2e6fb49e64a973e8799eef98dec1cb472
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361343"
---
# <a name="generic-text-mappings-in-tcharh"></a>Asignaciones de texto genérico en tchar.h

Para simplificar el transporte de código para uso internacional, la biblioteca en tiempo de ejecución de Microsoft proporciona asignaciones de texto genérico específicas de Microsoft para muchos tipos de datos, rutinas y otros objetos. Puede utilizar estas asignaciones, que se definen en tchar.h, para escribir código genérico que se puede compilar para conjuntos de caracteres `#define` unicode, multibyte o de un solo byte, en función de una constante de manifiesto que defina mediante una instrucción. Las asignaciones de texto genérico son extensiones de Microsoft que no son compatibles con ANSI.

Mediante el uso de tchar.h, puede crear aplicaciones de un solo byte, conjunto de caracteres multibyte (MBCS) y Unicode desde los mismos orígenes. tchar.h define macros (que `_tcs`tienen el prefijo) que, con `str`las `_mbs`definiciones de preprocesador correctas, se asignan a , , o `wcs` funciones, según corresponda. Para compilar MBCS, se ha de definir el símbolo `_MBCS`. Para crear Unicode, `_UNICODE`defina el símbolo . Para compilar una aplicación de un solo byte, no hay que definir ningún símbolo (opción predeterminada). De forma predeterminada, `_UNICODE` está definido para aplicaciones MFC.

El `_TCHAR` tipo de datos se define condicionalmente en tchar.h. Si el `_UNICODE` símbolo está definido `_TCHAR` para la compilación, se define como **wchar_t**; de lo contrario, para compilaciones de un solo byte y MBCS, se define como **char**. (**wchar_t**, el tipo de datos de caracteres anchos Unicode básico, es el homólogo de 16 bits a un **char**.8 bits firmado.) Para aplicaciones internacionales, utilice la `_tcs` familia `_TCHAR` de funciones, que funcionan en unidades, no en bytes. Por `_tcsncpy` ejemplo, `n` `_TCHARs`copia, no `n` bytes.

Dado que algunas funciones de control de cadenas de juego de caracteres de byte único (SBCS) reciben parámetros `char*` (con signo), se genera una advertencia del compilador indicando que el tipo no coincide cuando se define `_MBCS`. Hay tres formas de evitar esta advertencia:

1. Utilice la función en línea segura para tipos thunks en tchar.h. Este es el comportamiento predeterminado.

1. Utilice las macros directas en tchar.h definiendo `_MB_MAP_DIRECT` en la línea de comandos. Si lo hace, deberá hacer coincidir los tipos manualmente. Este es el método más rápido, pero no garantiza la seguridad de tipos.

1. Utilice la función de biblioteca vinculada estáticamente con seguridad de tipos thunks en tchar.h. Para ello, defina la constante `_NO_INLINING` en la línea de comandos. Este es el método más lento, pero garantiza prácticamente la seguridad de tipos.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Directivas de preprocesador para asignaciones de texto genérico

|# define|Versión compilada|Ejemplo|
|---------------|----------------------|-------------|
|`_UNICODE`|Unicode (carácter ancho)|`_tcsrev` se asigna a `_wcsrev`|
|`_MBCS`|Carácter multibyte|`_tcsrev` se asigna a `_mbsrev`|
|Ninguno (la opción predeterminada no tiene definidos `_UNICODE` ni `_MBCS`)|SBCS (ASCII)|`_tcsrev` se asigna a `strrev`|

Por ejemplo, `_tcsrev`la función de texto genérico, que se `_mbsrev` define `_MBCS` en tchar.h, se asigna a si ha definido en el programa o a `_wcsrev` si ha definido `_UNICODE`. De lo contrario, `_tcsrev` se asigna a `strrev`. Otras asignaciones de tipos de datos se proporcionan `_TCHAR` en tchar.h para mayor comodidad de programación, pero es la más útil.

### <a name="generic-text-data-type-mappings"></a>Asignaciones de tipos de datos de texto genérico

|Texto genérico <br /> Nombre de tipo de datos|_UNICODE &<br /> _MBCS no definidos|_MBCS<br /> Definido|_UNICODE<br /> Definido|
|--------------------------------------|----------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**char**|**char**|**wchar_t**|
|`_TINT`|**int**|**unsigned int**|`wint_t`|
|`_TSCHAR`|**signed char**|**signed char**|**wchar_t**|
|`_TUCHAR`|**unsigned char**|**unsigned char**|**wchar_t**|
|`_TXCHAR`|**char**|**unsigned char**|**wchar_t**|
|`_T` o `_TEXT`|Sin efecto (quitado por el preprocesador)|Sin efecto (quitado por el preprocesador)|`L`(convierte el siguiente carácter o cadena en su homólogo Unicode)|

Para obtener una lista de asignaciones de texto genérico de rutinas, variables y otros objetos, consulte [Asignaciones de texto genérico](../c-runtime-library/generic-text-mappings.md) en la Referencia de la biblioteca en tiempo de ejecución.

> [!NOTE]
> No utilice la familia `str` de funciones con cadenas de Unicode, ya que probablemente contendrán bytes nulos incrustados. Del mismo modo, no use la familia de funciones `wcs` con cadenas MBCS (o SBCS).

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

Si `_MBCS` ni `_UNICODE` se ha definido ni se han definido, el preprocesador asigna el fragmento al código ASCII de un solo byte, como se indica a continuación:

```cpp
char *RetVal, *szString;
RetVal = strrev(szString);
```

Por lo tanto, se puede crear, mantener y compilar un único archivo de código fuente para su ejecución con rutinas específicas de cualquiera de los tres tipos de juegos de caracteres.

## <a name="see-also"></a>Consulte también

[Texto y cadenas](../text/text-and-strings-in-visual-cpp.md)<br/>
[Uso de TCHAR. H Tipos de datos con código de _MBCS](../text/using-tchar-h-data-types-with-mbcs-code.md)
