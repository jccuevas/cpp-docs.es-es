---
title: wcstombs_s, _wcstombs_s_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcstombs_s_l
- wcstombs_s
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcstombs_s
- _wcstombs_s_l
dev_langs:
- C++
helpviewer_keywords:
- wcstombs_s function
- string conversion, wide characters
- wide characters, converting
- _wcstombs_s_l function
- wcstombs_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 105f2d33-221a-4f6d-864c-23c1865c42af
caps.latest.revision: 31
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: c407068c475f866062f8973fbacf70fcf6e6cae9
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="wcstombss-wcstombssl"></a>wcstombs_s, _wcstombs_s_l
Convierte una secuencia de caracteres anchos en una secuencia correspondiente de caracteres multibyte. Versión de [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count   
);  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t wcstombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _wcstombs_s_l(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pReturnValue`  
 El número de caracteres convertidos.  
  
 [out] `mbstr`  
 Dirección de un búfer para la cadena de caracteres multibyte convertida resultante.  
  
 [in]`sizeInBytes`  
 Tamaño del búfer `mbstr` en bytes.  
  
 [in] `wcstr`  
 Apunta a la cadena de caracteres anchos que se va a convertir.  
  
 [in] `count`  
 Número máximo de bytes que se van a almacenar en el búfer `mbstr`, sin incluir el carácter nulo de finalización, o [_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 [in] `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|---------------------|------------------------------|  
|`mbstr` es `NULL` y `sizeInBytes` > 0|`EINVAL`|  
|`wcstr` es `NULL`|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que `count` sea `_TRUNCATE`; vea la sección Comentarios a continuación)|`ERANGE`|  
  
 Si se produce alguna de estas condiciones, se invoca a la excepción de parámetro no válido, como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se permite que la ejecución continúe, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcstombs_s` convierte una cadena de caracteres anchos a la que apunta `wcstr` en caracteres multibyte almacenados en el búfer al que apunta `mbstr`. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:  
  
-   Se encuentre un carácter ancho nulo  
  
-   Se encuentre un carácter ancho que no se pueda convertir  
  
-   El número de bytes almacenados en el búfer `mbstr` sea igual a `count`.  
  
 La cadena de destino siempre tiene un carácter final nulo (aun en caso de error).  
  
 Si `count` es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), `wcstombs_s` convierte la parte de la cadena que quepa en el búfer de destino, a la vez que deja espacio para un carácter nulo final.  
  
 Si `wcstombs_s` convierte correctamente la cadena de origen, pone el tamaño en bytes de la cadena convertida, incluido el carácter final nulo, en `*``pReturnValue` (siempre que `pReturnValue` no sea `NULL`). Esto ocurre aunque el argumento `mbstr` sea `NULL` y permite determinar el tamaño de búfer necesario. Observe que si `mbstr` es `NULL`, `count` se omite.  
  
 Si `wcstombs_s` encuentra un carácter ancho que no pueda convertir en un carácter multibyte, pone 0 en `*``pReturnValue`, establece el búfer de destino en una cadena vacía, establece `errno` en `EILSEQ` y devuelve `EILSEQ`.  
  
 Si las secuencias señaladas por `wcstr` y `mbstr` se superponen, el comportamiento de `wcstombs_s` no está definido.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superpongan y de que `count` refleje correctamente el número de caracteres anchos que se van a convertir.  
  
 `wcstombs_s` usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; `_wcstombs_s_l` es igual que `wcstombs`, salvo que en su lugar usa la configuración regional pasada. Para más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcstombs_s`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Este programa muestra el comportamiento de la función `wcstombs_s`.  
  
```  
// crt_wcstombs_s.c  
// This example converts a wide character  
// string to a multibyte character string.  
#include <stdio.h>  
#include <stdlib.h>  
#include <assert.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t   i;  
    char      *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t*pWCBuffer = L"Hello, world.";  
  
    printf( "Convert wide-character string:\n" );  
  
    // Conversion  
    wcstombs_s(&i, pMBBuffer, (size_t)BUFFER_SIZE,   
               pWCBuffer, (size_t)BUFFER_SIZE );  
  
    // Output  
    printf("   Characters converted: %u\n", i);  
    printf("    Multibyte character: %s\n\n",  
     pMBBuffer );  
  
    // Free multibyte character buffer  
    if (pMBBuffer)  
    {  
    free(pMBBuffer);  
    }  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 14  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb_s, _wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
