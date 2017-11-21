---
title: wcsrtombs_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wcsrtombs_s
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
f1_keywords: wcsrtombs_s
dev_langs: C++
helpviewer_keywords:
- string conversion, wide characters
- wcsrtombs_s function
- wide characters, strings
ms.assetid: 9dccb766-113c-44bb-9b04-07a634dddec8
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f8045010875713588fb20a8f05a230717a21a9a9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="wcsrtombss"></a>wcsrtombs_s
Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte. Versión de [wcsrtombs](../../c-runtime-library/reference/wcsrtombs.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char *mbstr,  
   size_t sizeInBytes,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcsrtombs_s(  
   size_t *pReturnValue,  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pReturnValue`  
 El número de caracteres convertidos.  
  
 [out] `mbstr`  
 Dirección de un búfer para la cadena de caracteres multibyte convertida resultante.  
  
 [out] `sizeInBytes`  
 Tamaño del búfer `mbstr` en bytes.  
  
 [in] `wcstr`  
 Apunta a la cadena de caracteres anchos que se va a convertir.  
  
 [in] `count`  
 Número máximo de bytes que se almacenarán en el búfer `mbstr`, o [_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 [in] `mbstate`  
 Un puntero a un objeto `mbstate_t` de estado de la conversión.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|---------------------|------------------------------|  
|`mbstr` es `NULL` y `sizeInBytes` > 0|`EINVAL`|  
|`wcstr` es `NULL`|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida (a menos que `count` sea `_TRUNCATE`; vea la sección Comentarios a continuación)|`ERANGE`|  
  
 Si se produce alguna de estas condiciones, se invoca a la excepción de parámetro no válido, como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si se permite que la ejecución continúe, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcsrtombs_s` convierte una cadena de caracteres anchos a la que apunta `wcstr` en caracteres multibyte almacenados en el búfer al que apunta `mbstr`, mediante el estado de conversión incluido en `mbstate`. La conversión continuará para cada carácter hasta que se cumpla alguna de estas condiciones:  
  
-   Se encuentre un carácter ancho nulo  
  
-   Se encuentre un carácter ancho que no se pueda convertir  
  
-   El número de bytes almacenados en el búfer `mbstr` sea igual a `count`.  
  
 La cadena de destino siempre tiene un carácter final nulo (aun en caso de error).  
  
 Si `count` es el valor especial [_TRUNCATE](../../c-runtime-library/truncate.md), `wcsrtombs_s` convierte la parte de la cadena que quepa en el búfer de destino, a la vez que deja espacio para un carácter nulo final.  
  
 Si `wcsrtombs_s` convierte correctamente la cadena de origen, pone el tamaño en bytes de la cadena convertida, incluido el carácter final nulo, en `*pReturnValue` (siempre que `pReturnValue` no sea `NULL`). Esto ocurre aunque el argumento `mbstr` sea `NULL` y permite determinar el tamaño de búfer necesario. Observe que si `mbstr` es `NULL`, `count` se omite.  
  
 Si `wcsrtombs_s` encuentra un carácter ancho que no pueda convertir en un carácter multibyte, pone -1 en `*pReturnValue`, establece el búfer de destino en una cadena vacía, establece `errno` en `EILSEQ` y devuelve `EILSEQ`.  
  
 Si las secuencias señaladas por `wcstr` y `mbstr` se superponen, el comportamiento de `wcsrtombs_s` no está definido. `wcsrtombs_s` se ve afectado por la categoría LC_TYPE de la configuración regional actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superpongan y de que `count` refleje correctamente el número de caracteres anchos que se van a convertir.  
  
 La función `wcsrtombs_s` difiere de [wcstombs_s, _wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md) en que se puede reiniciar. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría `wcsrlen` en lugar de `wcslen` si se empleara una llamada subsiguiente a `wcsrtombs_s` en lugar de a `wcstombs_s.`  
  
 En C++, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Excepciones  
 La función `wcsrtombs_s` es segura para subprocesos siempre y cuando ninguna función del proceso actual llame a `setlocale` mientras se ejecuta esta función y `mbstate` sea nulo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_wcsrtombs_s.cpp  
//   
// This code example converts a wide  
// character string into a multibyte  
// character string.  
//  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
void main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    errno_t         err;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    err = wcsrtombs_s(&countConverted, mbString, MB_BUFFER_SIZE,  
                      &wcsIndirectString, MB_BUFFER_SIZE, &mbstate);  
    if (err == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfully converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfully converted.  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcsrtombs_s`|\<wchar.h>|  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)