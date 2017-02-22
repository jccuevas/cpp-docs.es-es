---
title: "_mbsnbcmp, _mbsnbcmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcmp"
  - "_mbsnbcmp_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "mbsnbcmp"
  - "tcsnbmp"
  - "_mbsnbcmp_l"
  - "mbsnbcmp_l"
  - "_mbsnbcmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcmp (función)"
  - "_mbsnbcmp_l (función)"
  - "_tcsncmp (función)"
  - "mbsnbcmp (función)"
  - "mbsnbcmp_l (función)"
  - "tcsncmp (función)"
ms.assetid: dbc99e50-cf85-4e57-a13f-067591f18ac8
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _mbsnbcmp, _mbsnbcmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara los primeros `n` bytes de dos cadenas de caracteres multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsnbcmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Las cadenas que se comparan.  
  
 `count`  
 El número de bytes que se compara.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 El valor devuelto indica la relación ordinal entre las subcadenas de `string1` y `string`.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|La subcadena `string1` es menor que la subcadena `string2`.|  
|0|La subcadena `string1` es idéntica a la subcadena `string2`.|  
|\> 0|La subcadena `string1` es mayor que la subcadena `string2`.|  
  
 Si se produce un error de validación de parámetros, `_mbsnbcmp` y `_mbsnbcmp_l` devuelven `_NLSCMPERROR`, que se define en \<string.h\> y \<mbstring.h\>.  
  
## Comentarios  
 Las funciones `_mbsnbcmp` comparan a lo sumo los primeros `count` bytes en `string1` y `string2`, y devuelven un valor que indica la relación entre las subcadenas.  `_mbsnbcmp` es una versión de `_mbsnbicmp` que distingue entre mayúsculas y minúsculas.  A diferencia de `_mbsnbcoll`, `_mbsnbcmp` no se ve afectado por el orden de intercalación de la configuración regional.  `_mbsnbcmp` reconoce secuencias de caracteres multibyte según la actual [página de códigos](../../c-runtime-library/code-pages.md) multibyte.  
  
 `_mbsnbcmp` es similar a `_mbsncmp`, salvo que `_mbsncmp` compara las cadenas por caracteres y no por bytes.  
  
 El valor de salida se ve afectado por la categoría `LC_CTYPE` de la configuración regional, que especifica los bytes iniciales y finales bytes de los caracteres multibyte.  Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  La función `_mbsnbcmp` usa la configuración regional actual para este comportamiento dependiente de dicha configuración.  La función `_mbsnbcmp_l` es idéntica, salvo que usa el parámetro `locale`.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `string1` o `string2` son un puntero nulo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven `_NLSCMPERROR` y `errno` se establece en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncmp`|[strncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|`_mbsnbcmp`|[wcsncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|  
|`_tcsncmp_l`|[strncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|`_mbsnbcml`|[wcsncmp](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbcmp`|\<mbstring.h\>|  
|`_mbsnbcmp_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_mbsnbcmp.c  
#include <mbstring.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n          %s\n", string1 );  
   printf( "          %s\n\n", string2 );  
   printf( "Function: _mbsnbcmp (first 10 characters only)\n" );  
   result = _mbsncmp( string1, string2 , 10 );  
   if( result > 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:   String 1 is %s string 2\n\n", tmp );  
   printf( "Function: _mbsnicmp _mbsnicmp (first 10 characters only)\n" );  
   result = _mbsnicmp( string1, string2, 10 );  
   if( result > 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      _mbscpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      _mbscpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:   String 1 is %s string 2\n\n", tmp );  
}  
```  
  
## Salida  
  
```  
Compare strings:  
          The quick brown dog jumps over the lazy fox  
          The QUICK brown fox jumps over the lazy dog  
  
Function: _mbsnbcmp (first 10 characters only)  
Result:   String 1 is greater than string 2  
  
Function: _mbsnicmp _mbsnicmp (first 10 characters only)  
Result:   String 1 is equal to string 2  
```  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [\_mbsnbicmp, \_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)