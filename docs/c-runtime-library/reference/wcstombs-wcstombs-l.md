---
title: wcstombs, _wcstombs_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcstombs
- _wcstombs_l
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
- wcstombs
- _wcstombs_l
dev_langs:
- C++
helpviewer_keywords:
- _wcstombs_l function
- wcstombs function
- string conversion, wide characters
- wide characters, converting
- wcstombs_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 91234252-9ea1-423a-af99-e9d0ce4a40e3
caps.latest.revision: 30
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 200337a53155b27b76a944d025c8fb013c29c4e6
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="wcstombs-wcstombsl"></a>wcstombs, _wcstombs_l
Convierte una secuencia de caracteres anchos en una secuencia correspondiente de caracteres multibyte. Hay disponibles versiones más seguras de estas funciones; vea [wcstombs_s, _wcstombs_s_l](../../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t wcstombs(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count   
);  
size_t _wcstombs_l(  
   char *mbstr,  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
size_t wcstombs(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count   
); // C++ only  
template <size_t size>  
size_t _wcstombs_l(  
   char (&mbstr)[size],  
   const wchar_t *wcstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 `mbstr`  
 Dirección de una secuencia de caracteres multibyte.  
  
 `wcstr`  
 Dirección de una secuencia de caracteres anchos.  
  
 `count`  
 Número máximo de bytes que se pueden almacenar en la cadena de salida multibyte.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si `wcstombs` convierte correctamente la cadena multibyte, devuelve el número de bytes escritos en la cadena de salida multibyte, sin incluir el carácter final `NULL` (si lo hubiera). Si el argumento `mbstr` es `NULL`, `wcstombs` devuelve el tamaño necesario en bytes de la cadena de destino. Si `wcstombs` encuentra un carácter ancho que no se puede convertir en un carácter multibyte, devuelve -1 que se convierte al tipo `size_t` y establece `errno` a `EILSEQ`.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcstombs` convierte la cadena de caracteres anchos a la que apunta `wcstr` en los caracteres multibyte correspondientes y almacena los resultados en la matriz `mbstr`. El parámetro `count` indica el número máximo de bytes que se pueden almacenar en la cadena de salida multibyte (es decir, el tamaño de `mbstr`). En general, no se conoce el número de bytes que se necesitarán al convertir una cadena de caracteres anchos. Algunos caracteres anchos necesitarán un solo byte de la cadena de salida; otros necesitarán dos. Si hay dos bytes en la cadena de salida multibyte por cada carácter ancho de la cadena de entrada (incluido el carácter ancho `NULL`), el resultado cabe seguro.  
  
 Si `wcstombs` encuentra el carácter nulo ancho (L'\0') mientras se produce `count` o antes, lo convierte en un 0 de 8 bits y se detiene. Por tanto, la cadena de caracteres multibyte en `mbstr` tiene un carácter de fin nulo solo si `wcstombs` encuentra un carácter ancho nulo durante la conversión. Si las secuencias señaladas por `wcstr` y `mbstr` se superponen, el comportamiento de `wcstombs` no está definido.  
  
 Si el argumento `mbstr` es `NULL`, `wcstombs` devuelve el tamaño necesario en bytes de la cadena de destino.  
  
 `wcstombs` valida sus parámetros. Si `wcstr` es `NULL`, o si `count` es mayor que `INT_MAX`, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md) . Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve -1.  
  
 `wcstombs` usa la configuración regional actual para cualquier comportamiento dependiente de la configuración regional; `_wcstombs_l` es igual, salvo que en su lugar usa la configuración regional pasada. Para más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C++, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcstombs`|\<stdlib.h>|  
|`_wcstombs_l`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Este programa muestra el comportamiento de la función `wcstombs`.  
  
```  
// crt_wcstombs.c  
// compile with: /W3  
// This example demonstrates the use  
// of wcstombs, which converts a string  
// of wide characters to a string of   
// multibyte characters.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
#define BUFFER_SIZE 100  
  
int main( void )  
{  
    size_t  count;  
    char    *pMBBuffer = (char *)malloc( BUFFER_SIZE );  
    wchar_t *pWCBuffer = L"Hello, world.";  
  
    printf("Convert wide-character string:\n" );  
  
    count = wcstombs(pMBBuffer, pWCBuffer, BUFFER_SIZE ); // C4996  
    // Note: wcstombs is deprecated; consider using wcstombs_s instead  
    printf("   Characters converted: %u\n",  
            count );  
    printf("    Multibyte character: %s\n\n",  
           pMBBuffer );  
  
    free(pMBBuffer);  
}  
```  
  
```Output  
Convert wide-character string:  
   Characters converted: 13  
    Multibyte character: Hello, world.  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
