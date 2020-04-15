---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364467"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Obtiene la longitud de una cadena usando la configuración regional actual o una que se haya pasado. Se trata de versiones más seguras de [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen**, **_mbsnlen_l**, **_mbstrnlen**y **_mbstrnlen_l** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Cadena terminada en un valor nulo.

*numberOfElements*<br/>
Tamaño del búfer de cadena.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Estas funciones devuelven el número de caracteres de la cadena, sin incluir el carácter null de terminación. Si no hay ningún terminador nulo dentro del primer *numberOfElements* bytes de la cadena (o caracteres anchos para **wcsnlen**), se devuelve *numberOfElements* para indicar la condición de error; las cadenas terminadas en null tienen longitudes que son estrictamente menores que *numberOfElements*.

**_mbstrnlen** y **_mbstrnlen_l** devuelven -1 si la cadena contiene un carácter multibyte no válido.

## <a name="remarks"></a>Observaciones

> [!NOTE]
> **strnlen** no es un reemplazo para **strlen**; **strnlen** está pensado para ser utilizado solamente para calcular el tamaño de los datos entrantes no confiables en un buffer del tamaño conocido— por ejemplo, un paquete de red. **strnlen** calcula la longitud, pero no pasa por el final del búfer si la cadena no está terminada. Para otras situaciones, utilice **strlen**. (Lo mismo se aplica a **wcsnlen**, **_mbsnlen**, y **_mbstrnlen**.)

Cada una de estas funciones devuelve el número de caracteres en *str*, sin incluir el carácter nulo de terminación. Sin embargo, **strnlen** y **strnlen_s** interpretar la cadena como una cadena de caracteres de un solo byte y, por lo tanto, el valor devuelto siempre es igual al número de bytes, incluso si la cadena contiene caracteres multibyte. **wcsnlen** y **wcsnlen_s** son versiones de caracteres anchos de **strnlen** y **strnlen_s** respectivamente; los argumentos para **wcsnlen** y **wcsnlen_s** son cadenas de caracteres anchos y el recuento de caracteres está en unidades de caracteres anchos. De lo contrario, **wcsnlen** y **strnlen** se comportan de forma idéntica, al igual que **strnlen_s** y **wcsnlen_s**.

**strnlen**, **wcsnlen**y **_mbsnlen** no validan sus parámetros. Si *str* es **NULL**, se produce una infracción de acceso.

**strnlen_s** y **wcsnlen_s** validar sus parámetros. Si *str* es **NULL**, las funciones devuelven 0.

**_mbstrnlen** también valida sus parámetros. Si *str* es **NULL**, o si *numberOfElements* es mayor que **INT_MAX**, **_mbstrnlen** genera una excepción de parámetro no válida, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **_mbstrnlen** establece **errno** en **EINVAL** y devuelve -1.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** y **_mbstrnlen** devolver el número de caracteres multibyte en una cadena de caracteres multibyte. **_mbsnlen** reconoce las secuencias de caracteres multibyte según la página de códigos multibyte que está actualmente en uso o según la configuración regional que se pasa; no prueba la validez de caracteres multibyte. **_mbstrnlen** pruebas de validez de caracteres multibyte y reconoce secuencias de caracteres multibyte. Si la cadena que se pasa a **_mbstrnlen** contiene un carácter multibyte no válido, **errno** se establece en **EILSEQ**.

El valor de salida se ve afectado por la configuración de la **LC_CTYPE** configuración de categoría de la configuración regional; ver [setlocale, _wsetlocale](setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, excepto que las que no tienen el **_l** sufijo usan la configuración regional actual para este comportamiento dependiente de la configuración regional y las versiones que tienen el **sufijo _l** en su lugar usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> o \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
