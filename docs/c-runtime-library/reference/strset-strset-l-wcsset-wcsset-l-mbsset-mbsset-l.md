---
title: "_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcsset"
  - "_mbsset"
  - "_strset_l"
  - "_strset"
  - "_wcsset_l"
  - "_mbsset_l"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "mbsset"
  - "_strset_l"
  - "_mbsset"
  - "_strset"
  - "mbsset_l"
  - "strset_l"
  - "_wcsset"
  - "_ftcsset"
  - "wcsset_l"
  - "_tcsset_l"
  - "_mbsset_l"
  - "_wcsset_l"
  - "_fstrset"
  - "_tcsset"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstrset (función)"
  - "_ftcsset (función)"
  - "_mbsset (función)"
  - "_mbsset_l (función)"
  - "_strset (función)"
  - "_strset_l (función)"
  - "_tcsset (función)"
  - "_tcsset_l (función)"
  - "_wcsset (función)"
  - "_wcsset_l (función)"
  - "caracteres [C++], establecer"
  - "fstrset (función)"
  - "ftcsset (función)"
  - "mbsset (función)"
  - "mbsset_l (función)"
  - "cadenas [C++], establecer caracteres"
  - "strset_l (función)"
  - "tcsset (función)"
  - "tcsset_l (función)"
  - "wcsset_l (función)"
ms.assetid: c42ded42-2ed9-4f06-a0a9-247ba305473a
caps.latest.revision: 31
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece los caracteres de una cadena en un carácter.  Hay disponibles versiones más seguras de estas funciones; vea [\_strset\_s, \_strset\_s\_l, \_wcsset\_s, \_wcsset\_s\_l, \_mbsset\_s, \_mbsset\_s\_l](../../c-runtime-library/reference/strset-s-strset-s-l-wcsset-s-wcsset-s-l-mbsset-s-mbsset-s-l.md).  
  
> [!IMPORTANT]
>  `_mbsset` y `_mbsset_l` no se pueden usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
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
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a establecer.  
  
 `c`  
 Especificación de carácter.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve un puntero a la cadena modificada.  
  
## Comentarios  
 La función `_strset` establece todos los caracteres \(excepto el carácter nulo de terminación\) de `str` en `c`, convertido en `char`.  `_wcsset` y `_mbsset_l` son versiones con caracteres anchos y versiones de caracteres multibyte de `_strset`, y los tipos de datos de los argumentos y los valores devueltos varían en consecuencia.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 `_mbsset` valida sus parámetros.  Si `str` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbsset` devuelve `NULL` y establece `errno` en `EINVAL`.  `_strset` y `_wcsset` no validan sus parámetros.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo `_l` usan la configuración regional actual y las que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
> [!IMPORTANT]
>  Estas funciones pueden ser vulnerables a amenazas de saturación del búfer.  Las saturaciones del búfer se pueden usar para ataques del sistema, ya que pueden producir una elevación de privilegios no justificada.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsset`|`_strset`|`_mbsset`|`_wcsset`|  
|`_tcsset_l`|`_strset_l`|`_mbsset_l`|`_wcsset_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strset`|\<string.h\>|  
|`_strset_l`|\<tchar.h\>|  
|`_wcsset`|\<string.h\> o \<wchar.h\>|  
|`_wcsset_l`|\<tchar.h\>|  
|`_mbsset`, `_mbsset_l`|\<mbstring.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
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
  
  **Antes: Fill the string with something.**  
**Después:  \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\***   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbset, \_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)