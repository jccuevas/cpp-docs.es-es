---
title: wcsrtombs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcsrtombs
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
- wcsrtombs
dev_langs:
- C++
helpviewer_keywords:
- wcsrtombs function
- string conversion, wide characters
- wide characters, strings
ms.assetid: a8d21fec-0d36-4085-9d81-9b1c61c7259d
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6dfe7e2293f9544b64a0dfd7dfaa1889e65a64dc
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="wcsrtombs"></a>wcsrtombs
Convierte una cadena de caracteres anchos en su representación de cadena de caracteres multibyte. Hay disponible una versión más segura de esta función; vea [wcsrtombs_s](../../c-runtime-library/reference/wcsrtombs-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t wcsrtombs(  
   char *mbstr,  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcsrtombs(  
   char (&mbstr)[size],  
   const wchar_t **wcstr,  
   sizeof count,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `mbstr`  
 Ubicación de la dirección de la cadena de caracteres multibyte convertida resultante.  
  
 [in] `wcstr`  
 Indirectamente apunta a la ubicación de la cadena de caracteres anchos que se va a convertir.  
  
 [in] `count`  
 Número de caracteres que se van a convertir.  
  
 [in] `mbstate`  
 Un puntero a un objeto `mbstate_t` de estado de la conversión.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de bytes convertidos correctamente, sin incluir el byte nulo de finalización (si lo hubiera), de lo contrario, -1 si se ha producido un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcsrtombs` convierte una cadena de caracteres anchos, a partir del estado de conversión especificado incluido en `mbstate`, de los valores a los que se apunta indirectamente en `wcstr`, en la dirección de `mbstr`. La conversión continuará para cada carácter hasta que: se encuentre un carácter ancho de finalización nulo, se encuentre un carácter no correspondiente o el siguiente carácter supere el límite incluido en `count`. Si `wcsrtombs` encuentra el carácter nulo ancho (L'\0') mientras se produce `count` o antes, lo convierte en un 0 de 8 bits y se detiene.  
  
 Por tanto, la cadena de caracteres multibyte en `mbstr` tiene un carácter de fin nulo solo si `wcsrtombs` encuentra un carácter ancho nulo durante la conversión. Si las secuencias señaladas por `wcstr` y `mbstr` se superponen, el comportamiento de `wcsrtombs` no está definido. `wcsrtombs` se ve afectado por la categoría LC_TYPE de la configuración regional actual.  
  
 La función `wcsrtombs` difiere de [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md) en que se puede reiniciar. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables.  Por ejemplo, una aplicación usaría `wcsrlen` en lugar de `wcsnlen` si se empleara una llamada subsiguiente a `wcsrtombs` en lugar de a `wcstombs`.  
  
 Si el argumento `mbstr` es `NULL`, `wcsrtombs` devuelve el tamaño necesario en bytes de la cadena de destino. Si `mbstate` es nulo, se usa el estado de conversión interno `mbstate_t`. Si la secuencia de caracteres `wchar` no tiene una representación de caracteres multibyte correspondiente, se devuelve el valor -1 y `errno` se establece a `EILSEQ`.  
  
 En C++, esta función tiene una sobrecarga de plantilla que invoca una contrapartida más nueva y segura de la función. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Excepciones  
 La función `wcsrtombs` es segura para subprocesos siempre y cuando ninguna función del proceso actual llame a `setlocale` mientras se ejecuta esta función y `mbstate` no sea nulo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_wcsrtombs.cpp  
// compile with: /W3  
// This code example converts a wide  
// character string into a multibyte  
// character string.  
  
#include <stdio.h>  
#include <memory.h>  
#include <wchar.h>  
#include <errno.h>  
  
#define MB_BUFFER_SIZE 100  
  
int main()  
{  
    const wchar_t   wcString[] =   
                    {L"Every good boy does fine."};  
    const wchar_t   *wcsIndirectString = wcString;  
    char            mbString[MB_BUFFER_SIZE];  
    size_t          countConverted;  
    mbstate_t       mbstate;  
  
    // Reset to initial shift state  
    ::memset((void*)&mbstate, 0, sizeof(mbstate));  
  
    countConverted = wcsrtombs(mbString, &wcsIndirectString,  
                               MB_BUFFER_SIZE, &mbstate); // C4996  
    // Note: wcsrtombs is deprecated; consider using wcsrtombs_s  
    if (errno == EILSEQ)  
    {  
        printf( "An encoding error was detected in the string.\n" );  
    }  
    else   
    {  
        printf( "The string was successfuly converted.\n" );  
    }  
}  
```  
  
```Output  
The string was successfuly converted.  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcsrtombs`|\<wchar.h>|  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
