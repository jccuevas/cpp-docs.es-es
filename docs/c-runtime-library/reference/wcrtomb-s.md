---
title: wcrtomb_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcrtomb_s
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
- wcrtomb_s
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb_s function
- multibyte characters
- characters, converting
ms.assetid: 9a8a1bd0-1d60-463d-a3a2-d83525eaf656
caps.latest.revision: 22
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: eec9f8620ed6533304568704444de6df33503818
ms.lasthandoff: 02/24/2017

---
# <a name="wcrtombs"></a>wcrtomb_s
Convierte un carácter ancho en su representación de carácter multibyte. Versión de [wcrtomb](../../c-runtime-library/reference/wcrtomb.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char *mbchar,  
   size_t sizeOfmbchar,  
   wchar_t *wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
errno_t wcrtomb_s(  
   size_t *pReturnValue,  
   char (&mbchar)[size],  
   wchar_t *wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `pReturnValue`  
 Devuelve el número de bytes escritos o -1 si se ha producido un error.  
  
 [out] `mbchar`  
 Carácter convertido multibyte resultante.  
  
 [in] `sizeOfmbchar`  
 Tamaño de la variable `mbchar` en bytes.  
  
 [in] `wchar`  
 Carácter ancho que se va a convertir.  
  
 [in] `mbstate`  
 Puntero a un objeto `mbstate_t` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve cero o un valor `errno` si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcrtomb_s` convierte un carácter ancho, a partir del estado de conversión especificado incluido en `mbstate`, del valor incluido en `wchar`, en la dirección representada por `mbchar`. El valor `pReturnValue` será el número de bytes convertidos, pero no más de `MB_CUR_MAX` bytes, o -1 si se ha producido un error.  
  
 Si `mbstate` es nulo, se usa el estado de conversión interno `mbstate_t`. Si el carácter incluido en `wchar` no tiene ningún carácter multibyte correspondiente, el valor de `pReturnValue` será -1 y la función devolverá el valor `errno` de `EILSEQ`.  
  
 La función `wcrtomb_s` difiere de [wctomb_s, _wctomb_s_l](../../c-runtime-library/reference/wctomb-s-wctomb-s-l.md) en que se puede reiniciar. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría `wcsrlen` en lugar de `wcslen` si se empleara una llamada subsiguiente a `wcsrtombs_s` en lugar de a `wcstombs_s.`  
  
 En C++, el uso de esta función se simplifica con las sobrecargas de plantilla; las sobrecargas pueden deducir automáticamente la longitud de búfer (lo que elimina el requisito de especificar un argumento de tamaño) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Excepciones  
 La función `wcrtomb_s` es segura para subprocesos siempre y cuando ninguna función del proceso actual llame a `setlocale` mientras se ejecuta esta función y `mbstate` sea nulo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_wcrtomb_s.c  
// This program converts a wide character  
// to its corresponding multibyte character.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    errno_t     returnValue;  
    size_t      pReturnValue;  
    mbstate_t   mbstate;  
    size_t      sizeOfmbStr = 1;  
    char        mbchar = 0;  
    wchar_t*    wchar = L"Q\0";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    returnValue = wcrtomb_s(&pReturnValue, &mbchar, sizeof(char),  
                            *wchar, &mbstate);  
    if (returnValue == 0) {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wchar);  
        printf(" was converted to a the \"%c\" ", mbchar);  
        printf("multibyte character.\n");  
    }  
    else  
    {  
        printf("No corresponding multibyte character "  
               "was found.\n");  
    }  
}  
```  
  
```Output  
The corresponding wide character "Q" was converted to a the "Q" multibyte character.  
```  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, consulte [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcrtomb_s`|\<wchar.h>|  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
