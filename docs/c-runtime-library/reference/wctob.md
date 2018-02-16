---
title: wctob | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- wctob
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
- wctob
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wctob function
- characters, converting
ms.assetid: 46aec98b-c2f2-4e9d-9d89-7db99ba8a9a6
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2534eb98c39be91ed753fdc0ff286a9a5c5ce707
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="wctob"></a>wctob
Determina si un carácter ancho se corresponde con un carácter multibyte y devuelve su representación de carácter multibyte.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int wctob(  
   wint_t wchar  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `wchar`  
 Valor que se va a traducir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si `wctob` convierte correctamente un carácter ancho, devuelve su representación de carácter multibyte únicamente si el carácter multibyte tiene una longitud exacta de un byte. Si `wctob` encuentra un carácter ancho que no se puede convertir en un carácter multibyte o el carácter multibyte no es exactamente un byte largo, devuelve -1.  
  
## <a name="remarks"></a>Comentarios  
 La función `wctob` convierte un carácter ancho incluido en `wchar` en el carácter multibyte correspondiente pasado por el valor devuelto `int` si el carácter multibyte tiene una longitud exacta de un byte.  
  
 Si `wctob` no se ha realizado correctamente y no se ha encontrado ningún carácter multibyte correspondiente, la función establece `errno` en `EILSEQ` y devuelve -1.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wctob`|\<wchar.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Este programa muestra el comportamiento de la función `wcstombs`.  
  
```  
// crt_wctob.c  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    int     bChar = 0;  
    wint_t  wChar = 0;  
  
    // Set the corresponding wide character to exactly one byte.  
    wChar = (wint_t)'A';  
  
    bChar = wctob( wChar );  
    if (bChar == WEOF)  
    {  
        printf( "No corresponding multibyte character was found.\n");  
    }  
    else  
    {  
        printf( "Determined the corresponding multibyte character to"  
                " be \"%c\".\n", bChar);  
    }  
}  
  
```  
  
```Output  
Determined the corresponding multibyte character to be "A".  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)