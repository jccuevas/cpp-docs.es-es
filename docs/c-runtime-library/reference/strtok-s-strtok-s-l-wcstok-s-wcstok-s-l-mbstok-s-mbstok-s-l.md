---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l
ms.date: 4/2/2020
api_name:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
- _o__mbstok_s
- _o__mbstok_s_l
- _o_strtok_s
- _o_wcstok_s
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
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
helpviewer_keywords:
- _strtok_s_l function
- _mbstok_s_l function
- strings [C++], searching
- mbstok_s_l function
- wcstok_s_l function
- _wcstok_s_l function
- _tcstok_s function
- _tcstok_s_l function
- strtok_s_l function
- wcstok_s function
- tokens, finding in strings
- mbstok_s function
- _mbstok_s function
- strtok_s function
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
ms.openlocfilehash: 9fe89fb897a5459b16c49060359b4bb40bc062a7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365216"
---
# <a name="strtok_s-_strtok_s_l-wcstok_s-_wcstok_s_l-_mbstok_s-_mbstok_s_l"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Busca el siguiente token en una cadena, con la configuración regional actual o con la configuración regional que se pase. Estas versiones de [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> **_mbstok_s** y **_mbstok_s_l** no se pueden usar en aplicaciones que se ejecutan en Windows Runtime. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
char* strtok_s(
   char* str,
   const char* delimiters,
   char** context
);

char* _strtok_s_l(
   char* str,
   const char* delimiters,
   char** context,
   _locale_t locale
);

wchar_t* wcstok_s(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context
);

wchar_t *_wcstok_s_l(
   wchar_t* str,
   const wchar_t* delimiters,
   wchar_t** context,
   _locale_t locale
);

unsigned char* _mbstok_s(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context
);

unsigned char* _mbstok_s_l(
   unsigned char* str,
   const unsigned char* delimiters,
   char** context,
   _locale_t locale
);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
Cadena que contiene el token o los tokens que se va a buscar.

*delimiters*<br/>
Conjunto de caracteres delimitadores que se van a utilizar.

*contextoo*<br/>
Se utiliza para almacenar información de posición entre llamadas a la función.

*locale*<br/>
Configuración regional que se va a usar.

## <a name="return-value"></a>Valor devuelto

Devuelve un puntero al siguiente token que se encuentra en *str*. Devuelve **NULL** cuando no se encuentran más tokens. Cada llamada modifica *str* sustituyendo un carácter nulo por el primer delimitador que se produce después del token devuelto.

### <a name="error-conditions"></a>Condiciones de error

|*Str*|*delimiters*|*contextoo*|Valor devuelto|**errno**|
|----------------|------------------|---------------|------------------|-------------|
|**Null**|cualquiera|puntero a un puntero nulo|**Null**|**EINVAL**|
|cualquiera|**Null**|cualquiera|**Null**|**EINVAL**|
|cualquiera|cualquiera|**Null**|**Null**|**EINVAL**|

Si *str* es **NULL** pero *context* es un puntero a un puntero de contexto válido, no hay ningún error.

## <a name="remarks"></a>Observaciones

La **strtok_s** strtok_s familia de funciones encuentra el siguiente token en *str*. El conjunto de caracteres en *los delimitadores* especifica los posibles delimitadores del token que se encuentra en *str* en la llamada actual. **wcstok_s** y **_mbstok_s** son versiones de caracteres anchos y multibyte de **strtok_s.** Los argumentos y valores devueltos de **wcstok_s** y **_wcstok_s_l** son cadenas de caracteres anchos; las de **_mbstok_s** y **_mbstok_s_l** son cadenas de caracteres multibyte. Por lo demás, estas funciones se comportan exactamente igual.

Esta función valida sus parámetros. Cuando se produce una condición de error, como en la tabla Condiciones de error, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen **errno en** **EINVAL** y devuelven **NULL**.

En la primera llamada a **strtok_s**, la función omite los delimitadores iniciales y devuelve un puntero al primer token de *str*, terminando el token con un carácter nulo. Más tokens se pueden romper del resto de *str* por una serie de llamadas a **strtok_s**. Cada llamada a **strtok_s** modifica *str* insertando un carácter nulo después del token devuelto por esa llamada. El puntero de *contexto* realiza un seguimiento de qué cadena se está leyendo y dónde se va a leer el siguiente token en la cadena. Para leer el siguiente token de *str*, llame a **strtok_s** con un valor **NULL** para el argumento *str* y pase el mismo parámetro *de contexto.* El argumento **NULL** *str* hace que **strtok_s** busque el siguiente token en el *str*modificado. El argumento *delimiters* puede tomar cualquier valor de una llamada a la siguiente para que el conjunto de delimitadores pueda variar.

Dado que el parámetro *context* reemplaza los búferes estáticos utilizados en **strtok** y **_strtok_l**, es posible analizar dos cadenas simultáneamente en el mismo subproceso.

El valor de salida se ve afectado por la configuración de la configuración de **categoría de LC_CTYPE** de la configuración regional. Para obtener más información, vea [setlocale](setlocale-wsetlocale.md).

Las versiones de estas funciones sin el **_l** sufijo utilizan la configuración regional de subprocesos actual para este comportamiento dependiente de la configuración regional. Las versiones con el sufijo **_l** son idénticas, excepto que en su lugar utilizan la configuración regional especificada por el parámetro *de configuración* regional. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**strtok_s**|\<string.h>|
|**_strtok_s_l**|\<string.h>|
|**wcstok_s**,<br />**_wcstok_s_l**|\<string.h> o \<wchar.h>|
|**_mbstok_s**,<br />**_mbstok_s_l**|\<mbstring.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|\_UNICODE \_& MBCS no definido|\_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcstok_s**|**strtok_s**|**_mbstok_s**|**wcstok_s**|
|**_tcstok_s_l**|**_strtok_s_l**|**_mbstok_s_l**|**_wcstok_s_l**|

## <a name="example"></a>Ejemplo

```C
// crt_strtok_s.c
// In this program, a loop uses strtok_s
// to print all the tokens (separated by commas
// or blanks) in two strings at the same time.

#include <string.h>
#include <stdio.h>

char string1[] =
    "A string\tof ,,tokens\nand some  more tokens";
char string2[] =
    "Another string\n\tparsed at the same time.";
char seps[]   = " ,\t\n";
char *token1 = NULL;
char *token2 = NULL;
char *next_token1 = NULL;
char *next_token2 = NULL;

int main(void)
{
    printf("Tokens:\n");

    // Establish string and get the first token:
    token1 = strtok_s(string1, seps, &next_token1);
    token2 = strtok_s(string2, seps, &next_token2);

    // While there are tokens in "string1" or "string2"
    while ((token1 != NULL) || (token2 != NULL))
    {
        // Get next token:
        if (token1 != NULL)
        {
            printf(" %s\n", token1);
            token1 = strtok_s(NULL, seps, &next_token1);
        }
        if (token2 != NULL)
        {
            printf("        %s\n", token2);
            token2 = strtok_s(NULL, seps, &next_token2);
        }
    }
}
```

```Output
Tokens:
A
        Another
string
        string
of
        parsed
tokens
        at
and
        the
some
        same
more
        time.
tokens
```

## <a name="see-also"></a>Consulte también

[Manipulación de cuerdas](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[strcspn, wcscspn, _mbscspn, _mbscspn_l](strcspn-wcscspn-mbscspn-mbscspn-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
