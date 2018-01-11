---
title: strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstok_s_l
- _mbstok_s_l
- _mbstok_s
- strtok_s
- wcstok_s
- _strtok_s_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstok_s_l
- _wcstok_s_l
- _tcstok_s
- _mbstok_s_l
- strtok_s
- wcstok_s
- _mbstok_s
- _strtok_s_l
dev_langs: C++
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
caps.latest.revision: "28"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e5d5b92497bedcfd766975e62c886dd64676fc71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="strtoks-strtoksl-wcstoks-wcstoksl-mbstoks-mbstoksl"></a>strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l

Busca el siguiente token en una cadena, con la configuración regional actual o con la configuración regional que se pase. Estas versiones de [strtok, _strtok_l, wcstok, _wcstok_l, _mbstok, _mbstok_l](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) incluyen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbstok_s` y `_mbstok_s_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```
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

unsigned char* _mbstok_s(  
   unsigned char* str,  
   const unsigned char* delimiters,   
   char** context,  
   _locale_t locale  
);  
```  
  
### <a name="parameters"></a>Parámetros  

*str*  
Una cadena que contiene el símbolo (token) o los tokens para buscar.  
  
*delimitadores*  
El conjunto de caracteres de delimitador que se va a usar.  
  
*contexto*  
Se utiliza para almacenar información de posición entre llamadas a la función.  
  
*locale*  
Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  

Devuelve un puntero al siguiente token que se encuentra en *str*. Devuelve `NULL` cuando no se encuentren más tokens. Cada llamada modifica *str* al sustituir una `NULL` caracteres para el primer delimitador que aparece después del token devuelto.  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|*str*|*delimitadores*|*contexto*|Valor devuelto|`errno`|  
|----------------|------------------|---------------|------------------|-------------|  
|`NULL`|any|puntero a un puntero nulo|`NULL`|`EINVAL`|  
|any|`NULL`|any|`NULL`|`EINVAL`|  
|any|any|`NULL`|`NULL`|`EINVAL`|  
  
Si *str* es `NULL` pero *contexto* es un puntero a un puntero de contexto válido, no hay ningún error.  
  
## <a name="remarks"></a>Comentarios  

El `strtok_s` familia de funciones busca el siguiente token en *str*. El juego de caracteres en *delimitadores* especifica los delimitadores posibles del token que se encuentren en *str* en la llamada actual. `wcstok_s` y `_mbstok_s` son versiones de caracteres anchos y multibyte de `strtok_s`. Los argumentos y valores devueltos de `wcstok_s` y `_wcstok_s_l` son cadenas de caracteres anchos; los de `_mbstok_s` y `_mbstok_s_l` son cadenas de caracteres multibyte. Por lo demás, estas funciones se comportan exactamente igual.  

Esta función valida sus parámetros. Si se produce una condición de error, como se describe en la tabla de condiciones de error, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `NULL`.

En la primera llamada a `strtok_s` la función omite los delimitadores iniciales y devuelve un puntero al primer token de *str*, finaliza el token con un carácter nulo. Más tokens se pueden extraer el resto de *str* mediante una serie de llamadas a `strtok_s`. Cada llamada a `strtok_s` modifica *str* insertando un carácter nulo después del token devuelto por la llamada. El *contexto* puntero realiza un seguimiento de la cadena que se está leyendo y dónde en la cadena siguiente token se leerá. Para leer el token siguiente de *str*, llame a `strtok_s` con un `NULL` valor para el *str* argumento y pase el mismo *contexto* parámetro. El `NULL` *str* argumento causas `strtok_s` para buscar el siguiente token en modificados *str*. El *delimitadores* argumento acepta cualquier valor de una llamada a la siguiente para que el juego de delimitadores puede variar.

Puesto que la *contexto* parámetro reemplaza los búferes estáticos que se usan en `strtok` y `_strtok_l`, es posible analizar dos cadenas simultáneamente en el mismo subproceso.

El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones sin el `_l` sufijo usar la configuración regional del subproceso actual para este comportamiento dependiente de la configuración regional. Las versiones con el `_l` sufijo son idénticas salvo que usan en su lugar el *configuración regional* parámetro. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`strtok_s`|\<string.h>|
|`_strtok_s_l`|\<string.h>|
|`wcstok_s`,<br />`_wcstok_s_l`|\<string.h> o \<wchar.h>|
|`_mbstok_s`,<br />`_mbstok_s_l`|\<mbstring.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|\_UNICODE & \_MBCS sin definir|\_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|

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
  
## <a name="see-also"></a>Vea también  

[Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)  
[Configuración regional](../../c-runtime-library/locale.md)  
[Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)  
[strcspn, wcscspn, _mbscspn, _mbscspn_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)  
[strspn, wcsspn, _mbsspn, _mbsspn_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)