---
title: strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l
ms.date: 11/04/2016
apiname:
- strxfrm
- _wcsxfrm_l
- _strxfrm_l
- wcsxfrm
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 4e4f5bb6639cbeee0f004f94f09177c08394d43e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50590988"
---
# <a name="strxfrm-wcsxfrm-strxfrml-wcsxfrml"></a>strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l

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
Número máximo de caracteres que se va a colocar en *strDest*.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve la longitud de la cadena transformada, sin contar el carácter nulo de terminación. Si el valor devuelto es mayor o igual a *recuento*, el contenido de *strDest* es imprevisible. Produce un error, cada función establece **errno** y devuelve **INT_MAX**. Para un carácter no válido, **errno** está establecido en **EILSEQ**.

## <a name="remarks"></a>Comentarios

El **strxfrm** función transforma la cadena señalada por *strSource* en un nuevo formulario intercalado que se almacena en *strDest*. No más de *recuento* caracteres, incluido el carácter nulo, se transforman y se colocan en la cadena resultante. La transformación se realiza mediante la configuración regional **LC_COLLATE** valor de la categoría. Para obtener más información sobre **LC_COLLATE**, consulte [setlocale](setlocale-wsetlocale.md). **strxfrm** usa la configuración regional actual para su comportamiento dependiente de la configuración regional; **_strxfrm_l** es idéntico, salvo que usa la configuración regional pasada en lugar de la configuración regional actual. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

Después de la transformación, una llamada a **strcmp** con las dos cadenas transformadas produce resultados idénticos a los de una llamada a **strcoll** aplicado a las dos cadenas originales. Igual que con **strcoll** y **stricoll**, **strxfrm** controla automáticamente las cadenas de caracteres multibyte según corresponda.

**wcsxfrm** es una versión con caracteres anchos de **strxfrm**; los argumentos de cadena de **wcsxfrm** son punteros de caracteres anchos. Para **wcsxfrm**, después la transformación de cadena, una llamada a **wcscmp** con las dos cadenas transformadas produce resultados idénticos a los de una llamada a **wcscoll** aplicado a la dos cadenas originales. **wcsxfrm** y **strxfrm** se comportan exactamente igual. **wcsxfrm** usa la configuración regional actual para su comportamiento dependiente de la configuración regional; **_wcsxfrm_l** usa la configuración regional pasada en lugar de la configuración regional actual.

Estas funciones validan sus parámetros. Si *strSource* es un puntero nulo, o *strDest* es un **NULL** puntero (a menos que el recuento es cero), o si *recuento* es mayor que **INT_MAX**, se invoca el controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, estas funciones establecen **errno** a **EINVAL** y devolver **INT_MAX**.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsxfrm**|**strxfrm**|**strxfrm**|**wcsxfrm**|
|**_tcsxfrm_l**|**_strxfrm_l**|**_strxfrm_l**|**_wcsxfrm_l**|

En la configuración regional "C", el orden de los caracteres del juego de caracteres (juego de caracteres ASCII) es el mismo que el orden lexicográfico de los caracteres. Sin embargo, en otras configuraciones regionales, el orden de los caracteres del juego de caracteres puede diferir del orden lexicográfico de los caracteres. Por ejemplo, en determinadas configuraciones regionales europeas, el carácter 'a' (valor 0 x 61) precede el carácter ' &\#x00E4;' (valor 0xE4) en el juego de caracteres, pero el carácter 'Unicote?' precede al carácter "a" lexicográficamente.

En las configuraciones regionales para el que el juego de caracteres y el orden lexicográfico de los caracteres son diferentes, utilice **strxfrm** en las cadenas originales y, a continuación, **strcmp** en las cadenas resultantes para generar una cadena lexicográfica comparación según la configuración regional actual **LC_COLLATE** valor de la categoría. Por lo tanto, para comparar dos cadenas de manera lexicográfica en la configuración regional anterior, use **strxfrm** en las cadenas originales y, a continuación, **strcmp** en las cadenas resultantes. Como alternativa, puede usar **strcoll** lugar **strcmp** en las cadenas originales.

**strxfrm** es básicamente un contenedor en torno a [LCMapString](/windows/desktop/api/winnls/nf-winnls-lcmapstringa) con **LCMAP_SORTKEY**.

El valor de la siguiente expresión es el tamaño de la matriz necesaria para albergar el **strxfrm** transformación de la cadena de origen:

`1 + strxfrm( NULL, string, 0 )`

En la configuración regional "C", **strxfrm** equivale a lo siguiente:

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
