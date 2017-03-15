---
title: "strncmp, wcsncmp, _mbsncmp, _mbsncmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
  - "_mbsncmp_l"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ftcsnccmp"
  - "_ftcsncmp"
  - "_tcsncmp"
  - "_tcsnccmp"
  - "strncmp"
  - "_mbsncmp"
  - "wcsncmp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ftcsnccmp (función)"
  - "_ftcsncmp (función)"
  - "_mbsncmp (función)"
  - "_mbsncmp_l (función)"
  - "_tcsnccmp (función)"
  - "_tcsncmp (función)"
  - "caracteres [C++], comparar"
  - "ftcsnccmp (función)"
  - "ftcsncmp (función)"
  - "mbsncmp (función)"
  - "mbsncmp_l (función)"
  - "comparación de cadenas [C++], strncmp (función)"
  - "cadenas [C++], comparar caracteres de"
  - "strncmp (función)"
  - "tcsnccmp (función)"
  - "tcsncmp (función)"
  - "wcsncmp (función)"
ms.assetid: 2fdbf4e6-77da-4b59-9086-488f6066b8af
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# strncmp, wcsncmp, _mbsncmp, _mbsncmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compara dos cadenas hasta el número especificado de caracteres.  
  
> [!IMPORTANT]
>  `_mbsncmp` y `_mbsncmp_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int strncmp(  
   const char *string1,  
   const char *string2,  
   size_t count   
);  
int wcsncmp(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   size_t count   
);  
int _mbsncmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
int _mbsncmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count,   
   _locale_t locale  
);int _mbsnbcmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Cadenas que se van a comparar.  
  
 `count`  
 Número de caracteres que se van a comparar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 El valor devuelto indica la relación de las subcadenas de `string1` y de `string2` como se indica a continuación.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|La subcadena `string1` es menor que la subcadena `string2`.|  
|0|La subcadena `string1` es idéntica a la subcadena `string2`.|  
|\> 0|La subcadena `string1` es mayor que la subcadena `string2`.|  
  
 Si se produce un error de validación de parámetros, `_mbsncmp` y `_mbsncmp_l` devuelven `_NLSCMPERROR`, que se define en \<string.h\> y \<mbstring.h\>.  
  
## Comentarios  
 La función `strncmp` realiza una comparación ordinal de, a lo sumo, `count` caracteres de `string1` y `string2`, y devuelve un valor que indica la relación entre ambas subcadenas.  `strncmp` es una versión de `_strnicmp` que distingue entre mayúsculas y minúsculas.  `wcsncmp` y `_mbsncmp` son versiones de `_wcsnicmp` y `_mbsnicmp` que distinguen entre mayúsculas y minúsculas.  
  
 `wcsncmp` y `_mbsncmp` son versiones de caracteres anchos y multibyte de `strncmp`.  Los argumentos de `wcsncmp` son cadenas de caracteres anchos; los de `_mbsncmp` son cadenas de caracteres multibyte.  `_mbsncmp` reconoce secuencias de caracteres multibyte según una página de códigos multibyte y devuelve `_NLSCMPERROR` cuando se produce un error.  
  
 Además, `_mbsncmp` y `_mbsncmp_l` validan parámetros.  Si `string1` o `string2` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `_mbsncmp` y `_mbsncmp_l` devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  `strncmp` y `wcsncmp` no validan sus parámetros.  Por lo demás, estas funciones se comportan exactamente igual.  
  
 El comportamiento de comparación de `_mbsncmp` y `_mbsncmp_l` se ve afectado por la configuración de la categoría `LC_CTYPE` de la configuración regional.  Esta opción controla la detección de los bytes iniciales y finales de caracteres multibyte.  Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  La función `_mbsncmp` usa la configuración regional actual para este comportamiento dependiente de dicha configuración.  La función `_mbsncmp_l` es idéntica, salvo que usa el parámetro `locale`.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  Si la configuración regional es de un solo byte, el comportamiento de estas funciones es idéntico a `strncmp`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsnccmp`|`strncmp`|`_mbsncmp`|`wcsncmp`|  
|`_tcsncmp`|`strncmp`|`_mbsnbcmp`|`wcsncmp`|  
|`_tccmp`|Se asigna a una macro o una función insertada|`_mbsncmp`|Se asigna a una macro o una función insertada|  
|**No aplicable**|**No aplicable**|`_mbsncmp_l`|**No aplicable**|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strncmp`|\<string.h\>|  
|`wcsncmp`|\<string.h\> o \<wchar.h\>|  
|`_mbsncmp`, `_mbsncmp_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strncmp.c  
#include <string.h>  
#include <stdio.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown fox jumps over the lazy dog";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
   printf( "Compare strings:\n      %s\n      %s\n\n",  
           string1, string2 );  
   printf( "Function:   strncmp (first 10 characters only)\n" );  
   result = strncmp( string1, string2 , 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n\n", tmp );  
   printf( "Function:   strnicmp _strnicmp (first 10 characters only)\n" );  
   result = _strnicmp( string1, string2, 10 );  
   if( result > 0 )  
      strcpy_s( tmp, sizeof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, sizeof(tmp), "less than" );  
   else  
      strcpy_s( tmp, sizeof(tmp), "equal to" );  
   printf( "Result:      String 1 is %s string 2\n", tmp );  
}  
```  
  
  **Cadenas de la comparación:**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown fox jumps over the lazy dog**  
**Función:   strncmp \(10 primeros caracteres solo\)**  
**Resultado:      La cadena 1 es mayor que la cadena 2**  
**Función:   strnicmp \_strnicmp \(10 primeros caracteres solo\)**  
**Resultado:      La cadena 1 es igual a la cadena 2**   
## Equivalente en .NET Framework  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbsnbcmp, \_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_mbsnbicmp, \_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)