---
title: _strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wcsset
- _mbsset
- _strset_l
- _strset
- _wcsset_l
- _mbsset_l
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
- mbsset
- _strset_l
- _mbsset
- _strset
- mbsset_l
- strset_l
- _wcsset
- _ftcsset
- wcsset_l
- _tcsset_l
- _mbsset_l
- _wcsset_l
- _fstrset
- _tcsset
dev_langs:
- C++
helpviewer_keywords:
- _wcsset_l function
- _tcsset function
- wcsset_l function
- _ftcsset function
- characters [C++], setting
- _strset function
- ftcsset function
- strings [C++], setting characters
- mbsset function
- tcsset_l function
- _fstrset function
- mbsset_l function
- strset_l function
- _wcsset function
- _mbsset function
- _mbsset_l function
- tcsset function
- _strset_l function
- fstrset function
- _tcsset_l function
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
caps.latest.revision: 31
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
ms.openlocfilehash: 9db9c684f27f2cae103cf3071332a5d7fa90e8d9
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="strset-strsetl-wcsset-wcssetl-mbsset-mbssetl"></a>_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l
Establece los caracteres de una cadena en un carácter. Hay disponibles versiones más seguras de estas funciones; vea [_strset_s, _strset_s_l, _wcsset_s, _wcsset_s_l, _mbsset_s, _mbsset_s_l](../../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsset` y `_mbsset_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
char *_strset(  
   char *str,  
   int c   
);  
char *_strset_l(  
   char *str,  
   int c,  
   locale_t locale  
);  
wchar_t *_wcsset(  
   wchar_t *str,  
   wchar_t c   
);  
wchar_t *_wcsset_l(  
   wchar_t *str,  
   wchar_t c,  
   locale_t locale  
);  
unsigned char *_mbsset(  
   unsigned char *str,  
   unsigned int c   
);  
unsigned char *_mbsset_l(  
   unsigned char *str,  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `str`  
 Cadena terminada en NULL que se va a establecer.  
  
 `c`  
 Especificación de carácter.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la cadena modificada.  
  
## <a name="remarks"></a>Comentarios  
 La función `_strset` establece todos los caracteres (excepto el carácter nulo de terminación) de `str` en `c`, convertido en `char`. `_wcsset` y `_mbsset_l` son versiones con caracteres anchos y versiones de caracteres multibyte de `_strset`, y los tipos de datos de los argumentos y los valores devueltos varían en consecuencia. Por lo demás, estas funciones se comportan exactamente igual.  
  
 `_mbsset` valida sus parámetros. Si `str` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `_mbsset` devuelve `NULL` y establece `errno` en `EINVAL`. `_strset` y `_wcsset` no validan sus parámetros.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información. Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo `_l` usan la configuración regional actual y las que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
> [!IMPORTANT]
>  Estas funciones pueden ser vulnerables a amenazas de saturación del búfer. Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada. Para obtener más información, vea [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795)(Evitar saturaciones del búfer).  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcsset`|`_strset`|`_mbsset`|`_wcsset`|  
|`_tcsset_l`|`_strset_l`|`_mbsset_l`|`_wcsset_l`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_strset`|\<string.h>|  
|`_strset_l`|\<tchar.h>|  
|`_wcsset`|\<string.h> o \<wchar.h>|  
|`_wcsset_l`|\<tchar.h>|  
|`_mbsset`, `_mbsset_l`|\<mbstring.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_strset.c  
// compile with: /W3  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[] = "Fill the string with something.";  
   printf( "Before: %s\n", string );  
   _strset( string, '*' ); // C4996  
   // Note: _strset is deprecated; consider using _strset_s instead  
   printf( "After:  %s\n", string );  
}  
```  
  
```Output  
Before: Fill the string with something.  
After:  *******************************  
```  
  
## <a name="see-also"></a>Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [_mbsnbset, _mbsnbset_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat, wcscat, _mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, _mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [_strnset, _strnset_l, _wcsnset, _wcsnset_l, _mbsnset, _mbsnset_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)
