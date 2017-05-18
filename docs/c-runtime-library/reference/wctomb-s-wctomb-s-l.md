---
title: wctomb_s, _wctomb_s_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wctomb_s_l
- wctomb_s
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
- wctomb_s
- _wctomb_s_l
dev_langs:
- C++
helpviewer_keywords:
- wctomb_s function
- wctomb_s_l function
- string conversion, wide characters
- wide characters, converting
- _wctomb_s_l function
- characters, converting
- string conversion, multibyte character strings
ms.assetid: 7e94a888-deed-4dbd-b5e9-d4a0455538b8
caps.latest.revision: 18
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: ac97c0bc957c28d8d0837199157d52d4ac0536e1
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="wctombs-wctombsl"></a>wctomb_s, _wctomb_s_l
Convierte un carácter ancho en el carácter multibyte correspondiente. Versión de [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t wctomb_s(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar   
);  
errno_t _wctomb_s_l(  
   int *pRetValue,  
   char *mbchar,  
   size_t sizeInBytes,  
   wchar_t wchar,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pRetValue`  
 Número de bytes o un código que indica el resultado.  
  
 [out] `mbchar`  
 Dirección de un carácter multibyte.  
  
 [in] `sizeInBytes`  
 Tamaño del búfer `mbchar`.  
  
 [in] `wchar`  
 Carácter ancho.  
  
 [in] `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
 Condiciones de error  
  
|`mbchar`|`sizeInBytes`|Valor devuelto|`pRetValue`|  
|--------------|-------------------|------------------|-----------------|  
|`NULL`|>0|`EINVAL`|no modificado|  
|cualquiera|>`INT_MAX`|`EINVAL`|no modificado|  
|any|demasiado pequeño|`EINVAL`|no modificado|  
  
 Si se da alguna de las condiciones de error anteriores, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `wctomb` devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
## <a name="remarks"></a>Comentarios  
 La función `wctomb_s` convierte su argumento `wchar` en el carácter multibyte correspondiente y almacena el resultado en `mbchar`. Puede llamar a la función desde cualquier ubicación de cualquier programa.  
  
 Si `wctomb_s` convierte el carácter ancho en un carácter multibyte, coloca el número de bytes (que nunca es mayor que `MB_CUR_MAX`) en el carácter ancho en el entero al que apunta `pRetValue`. Si `wchar` es el carácter nulo ancho (L'\0'), `wctomb_s` rellena `pRetValue` con 1. Si el puntero de destino `mbchar` es NULL, `wctomb_s` pone 0 en `pRetValue`. Si la conversión no es posible en la configuración regional actual, `wctomb_s` pone -1 en `pRetValue`.  
  
 `wctomb_s` usa la configuración regional actual para la información dependiente de la configuración regional; `_wctomb_s_l` es igual, salvo que en su lugar usa la configuración regional pasada. Para más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wctomb_s`|\<stdlib.h>|  
|`_wctomb_s_l`|\<stdlib.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="example"></a>Ejemplo  
 Este programa muestra el comportamiento de la función `wctomb`.  
  
```  
// crt_wctomb_s.cpp  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
    int i;  
    wchar_t wc = L'a';  
    char *pmb = (char *)malloc( MB_CUR_MAX );  
  
    printf_s( "Convert a wide character:\n" );  
    wctomb_s( &i, pmb, MB_CUR_MAX, wc );  
    printf_s( "   Characters converted: %u\n", i );  
    printf_s( "   Multibyte character: %.1s\n\n", pmb );  
}  
```  
  
```Output  
Convert a wide character:  
   Characters converted: 1  
   Multibyte character: a  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [_mbclen, mblen, _mblen_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbstowcs, _mbstowcs_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md)   
 [mbtowc, _mbtowc_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, _wcstombs_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [WideCharToMultiByte](http://msdn.microsoft.com/library/windows/desktop/dd374130)
