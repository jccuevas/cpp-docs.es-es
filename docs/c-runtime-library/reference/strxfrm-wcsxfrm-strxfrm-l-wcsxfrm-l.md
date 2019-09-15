---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
api_name:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- strxfrm
- _tcsxfrm
- wcsxfrm
helpviewer_keywords:
- strxfrm_l function
- _tcsxfrm function
- _strxfrm_l function
- strxfrm function
- wcsxfrm_l function
- wcsxfrm function
- string comparison [C++], transforming strings
- tcsxfrm function
- strings [C++], comparing locale
- _wcsxfrm_l function
ms.assetid: 6ba8e1f6-4484-49aa-83b8-bc2373187d9e
ms.openlocfilehash: 411fe3a5a6f66614f0a22e0f623b73685a6e0844
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957605"
---
# <a name="strxfrm-wcsxfrm-_strxfrm_l-_wcsxfrm_l"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

Transforma una cadena en función de la información específica de la configuración regional.

## <a name="syntax"></a>Sintaxis

```C
size_t strxfrm(
   char *strDest,
   const char *strSource,
   size_t count
);
size_t wcsxfrm(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count
);
size_t _strxfrm_l(
   char *strDest,
   const char *strSource,
   size_t count,
   _locale_t locale
);
size_t wcsxfrm_l(
   wchar_t *strDest,
   const wchar_t *strSource,
   size_t count,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*strDest*<br/>
Cadena de destino.

*strSource*<br/>
Cadena de origen.

*count*<br/>
Número máximo de caracteres que se colocarán en *strDest*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la cadena transformada, sin contar el carácter nulo de terminación. Si el valor devuelto es mayor o igual que *Count*, el contenido de *strDest* es imprevisible. En un error, cada función establece **errno** y devuelve **INT_MAX**. Para un carácter no válido, **errno** se establece en **EILSEQ**.

## <a name="remarks"></a>Comentarios

La función **strxfrm** transforma la cadena a la que apunta *strSource* en un nuevo formulario intercalado que se almacena en *strDest*. No se transforman los caracteres de *recuento* , incluido el carácter nulo, y se colocan en la cadena resultante. La transformación se realiza mediante la configuración de la categoría **LC_COLLATE** de la configuración regional. Para obtener más información sobre **LC_COLLATE**, vea [setlocale](setlocale-wsetlocale.md). **strxfrm** usa la configuración regional actual para su comportamiento dependiente de la configuración regional; **_strxfrm_l** es idéntico, salvo que usa la configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Después de la transformación, una llamada a **strcmp** con las dos cadenas transformadas produce resultados idénticos a los de una llamada a **strcoll (** aplicada a las dos cadenas originales. Como con **strcoll (** y **stricoll**, **strxfrm** controla automáticamente las cadenas de caracteres multibyte según corresponda.

**wcsxfrm** es una versión con caracteres anchos de **strxfrm**; los argumentos de cadena de **wcsxfrm** son punteros de caracteres anchos. En el caso de **wcsxfrm**, después de la transformación de cadena, una llamada a **wcscmp** con las dos cadenas transformadas produce resultados idénticos a los de una llamada a **wcscoll** aplicada a las dos cadenas originales. **wcsxfrm** y **strxfrm** se comportan de manera idéntica. **wcsxfrm** usa la configuración regional actual para su comportamiento dependiente de la configuración regional; **_wcsxfrm_l** usa la configuración regional que se pasa en lugar de la configuración regional actual.

Estas funciones validan sus parámetros. Si *strSource* es un puntero nulo, o *strDest* es un puntero **nulo** (a menos que Count sea cero), o si *Count* es mayor que **INT_MAX**, se invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones establecen **errno** en **EINVAL** y devuelven **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

En la configuración regional "C", el orden de los caracteres del juego de caracteres (juego de caracteres ASCII) es el mismo que el orden lexicográfico de los caracteres. Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico de los caracteres. Por ejemplo, en determinadas configuraciones regionales europeas, el carácter "a" (valor 0x61) precede al carácter "&\#x00E4;". (valor 0xE4) en el juego de caracteres, pero el carácter ' ä ' precede al carácter ' a ' lexicográficamente.

En las configuraciones regionales en las que el conjunto de caracteres y el orden de los caracteres lexicográfico difieren, use **strxfrm** en las cadenas originales y, a continuación, **strcmp** en las cadenas resultantes para generar una comparación de cadenas lexicográfico según la configuración regional actual Configuración de la categoría **LC_COLLATE** . Por lo tanto, para comparar dos cadenas lexicográficamente en la configuración regional anterior, use **strxfrm** en las cadenas originales y después **strcmp** en las cadenas resultantes. Como alternativa, puede usar **strcoll (** en lugar de **strcmp** en las cadenas originales.

**strxfrm** es básicamente un contenedor alrededor de [LCMapString](/windows/win32/api/winnls/nf-winnls-lcmapstringw) con **LCMAP_SORTKEY**.

El valor de la siguiente expresión es el tamaño de la matriz necesaria para contener la transformación **strxfrm** de la cadena de origen:

`1 + strxfrm( NULL, string, 0 )`

En la configuración regional de "C", **strxfrm** es equivalente a lo siguiente:

```C
strncpy( _string1, _string2, _count );
return( strlen( _string1 ) );
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strxfrm**|\<string.h>|
|**wcsxfrm**|\<string.h> o \<wchar.h>|
|**_strxfrm_l**|\<string.h>|
|**_wcsxfrm_l**|\<string.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Conversión de datos](../../c-runtime-library/data-conversion.md)<br/>
[localeconv](localeconv.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strcmp, wcscmp, _mbscmp](strcmp-wcscmp-mbscmp.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
