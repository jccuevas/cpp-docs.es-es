---
title: wcrtomb | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- wcrtomb
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
- wcrtomb
dev_langs:
- C++
helpviewer_keywords:
- wide characters, converting
- wcrtomb function
- multibyte characters
- characters, converting
ms.assetid: 717f1b21-2705-4b7f-b6d0-82adc5224340
caps.latest.revision: 26
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 599802a3038305dd09fafb4b6fb278d05c13afa4
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="wcrtomb"></a>wcrtomb
Convierte un carácter ancho en su representación de carácter multibyte. Hay disponible una versión más segura de esta función; vea [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t wcrtomb(  
   char *mbchar,  
   wchar_t wchar,  
   mbstate_t *mbstate  
);  
template <size_t size>  
size_t wcrtomb(  
   char (&mbchar)[size],  
   wchar_t wchar,  
   mbstate_t *mbstate  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `mbchar`  
 Carácter convertido multibyte resultante.  
  
 [in] `wchar`  
 Carácter ancho que se va a convertir.  
  
 [in] `mbstate`  
 Puntero a un objeto `mbstate_t` .  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de bytes necesarios para representar el carácter multibyte convertido; si se produce un error, devuelve -1.  
  
## <a name="remarks"></a>Comentarios  
 La función `wcrtomb` convierte un carácter ancho, a partir del estado de conversión especificado incluido en `mbstate`, del valor incluido en `wchar`, en la dirección representada por `mbchar`. El valor devuelto es el número de bytes necesarios para representar el carácter multibyte correspondiente, pero no devolverá más de `MB_CUR_MAX` bytes.  
  
 Si `mbstate` es nulo, se usa el objeto interno `mbstate_t` que contiene el estado de conversión de `mbchar`. Si la secuencia de caracteres `wchar` no tiene una representación de caracteres multibyte correspondiente, se devuelve el valor -1 y `errno` se establece a `EILSEQ`.  
  
 La función `wcrtomb` difiere de [wctomb, _wctomb_l](../../c-runtime-library/reference/wctomb-wctomb-l.md) en que se puede reiniciar. El estado de la conversión se almacena en `mbstate` para llamadas posteriores a la misma o a otras funciones reiniciables. Los resultados no están definidos cuando se combina el uso de funciones reiniciables y no reiniciables. Por ejemplo, una aplicación usaría `wcsrlen` en lugar de `wcsnlen` si se empleara una llamada subsiguiente a `wcsrtombs` en lugar de a `wcstombs`.  
  
 En C++, esta función tiene una sobrecarga de plantilla que invoca a un homólogo más reciente y seguro de esta función. Para más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## <a name="exceptions"></a>Excepciones  
 La función `wcrtomb` es segura para subprocesos siempre y cuando ninguna función del proceso actual llame a `setlocale` mientras se ejecuta esta función y `mbstate` sea nulo.  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_wcrtomb.c  
// compile with: /W3  
// This program converts a wide character  
// to its corresponding multibyte character.  
  
#include <string.h>  
#include <stdio.h>  
#include <wchar.h>  
  
int main( void )  
{  
    size_t      sizeOfCovertion = 0;  
    mbstate_t   mbstate;  
    char        mbStr = 0;  
    wchar_t*    wcStr = L"Q";  
  
    // Reset to initial conversion state  
    memset(&mbstate, 0, sizeof(mbstate));  
  
    sizeOfCovertion = wcrtomb(&mbStr, *wcStr, &mbstate); // C4996  
    // Note: wcrtomb is deprecated; consider using wcrtomb_s instead  
    if (sizeOfCovertion > 0)  
    {  
        printf("The corresponding wide character \"");  
        wprintf(L"%s\"", wcStr);  
        printf(" was converted to the \"%c\" ", mbStr);  
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
The corresponding wide character "Q" was converted to the "Q" multibyte character.  
```  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wcrtomb`|\<wchar.h>|  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbsinit](../../c-runtime-library/reference/mbsinit.md)
