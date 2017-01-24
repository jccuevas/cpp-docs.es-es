---
title: "_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_stricmp_l"
  - "_mbsicmp"
  - "_wcsicmp"
  - "_mbsicmp_l"
  - "_stricmp"
  - "_wcsicmp_l"
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
  - "_ftcsicmp"
  - "_stricmp"
  - "wcsicmp_l"
  - "_wcsicmp"
  - "_tcsicmp"
  - "_strcmpi"
  - "stricmp_l"
  - "_mbsicmp"
  - "_fstricmp"
  - "mbsicmp_l"
  - "mbsicmp"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fstricmp (función)"
  - "_ftcsicmp (función)"
  - "_mbsicmp (función)"
  - "_mbsicmp_l (función)"
  - "_strcmpi (función)"
  - "_stricmp (función)"
  - "_stricmp_l (función)"
  - "_tcsicmp (función)"
  - "_wcsicmp (función)"
  - "_wcsicmp_l (función)"
  - "fstricmp (función)"
  - "ftcsicmp (función)"
  - "mbsicmp (función)"
  - "mbsicmp_l (función)"
  - "stricmp_l (función)"
  - "comparación de cadenas [C++], minúsculas"
  - "cadenas [C++], comparar"
  - "tcsicmp (función)"
  - "wcsicmp_l (función)"
ms.assetid: 0e1ee515-0d75-435a-a445-8875d4669b50
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Realiza una comparación de cadenas sin distinción entre mayúsculas y minúsculas.  
  
> [!IMPORTANT]
>  `_mbsicmp` y `_mbsicmp_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _stricmp(  
   const char *string1,  
   const char *string2   
);  
int _wcsicmp(  
   const wchar_t *string1,  
   const wchar_t *string2   
);  
int _mbsicmp(  
   const unsigned char *string1,  
   const unsigned char *string2   
);  
int _stricmp_l(  
   const char *string1,  
   const char *string2,  
   _locale_t locale  
);  
int _wcsicmp_l(  
   const wchar_t *string1,  
   const wchar_t *string2,  
   _locale_t locale  
);  
int _mbsicmp_l(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `string1, string2`  
 Cadenas terminadas en NULL que se van a comparar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 El valor devuelto indica la relación entre `string1` y `string2` como se indica a continuación.  
  
|Valor devuelto|Descripción|  
|--------------------|-----------------|  
|\< 0|`string1` es menor que `string2`|  
|0|`string1` es idéntica a `string2`|  
|\> 0|`string1` es mayor que `string2`|  
  
 En caso de error, `_mbsicmp` devuelve `_NLSCMPERROR`, que se define en \<string.h\> y \<mbstring.h\>.  
  
## Comentarios  
 La función `_stricmp` realiza una comparación ordinal de `string1` y `string2` después de convertir cada carácter a minúsculas y devuelve un valor que indica su relación.  `_stricmp` difiere de `_stricoll` en que la comparación `_stricmp` solo se ve afectada por `LC_CTYPE`, que determina qué caracteres van en mayúscula y cuáles en minúscula.  La función `_stricoll` compara las cadenas según las categorías `LC_CTYPE` y `LC_COLLATE` de la configuración regional, lo que incluye el uso de mayúsculas y minúsculas y el orden de intercalación.  Para obtener más información sobre la categoría `LC_COLLATE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) y [Categorías de configuración regional](../../c-runtime-library/locale-categories.md).  Las versiones de estas funciones sin el sufijo `_l` utilizan la configuración regional actual para el comportamiento que depende de la configuración regional.  Las versiones con el sufijo son idénticas, salvo que usan el parámetro de configuración regional que se pasa.  Si no se ha establecido la configuración regional, se utiliza la configuración regional de C.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
> [!NOTE]
>  `_stricmp` es equivalente a `_strcmpi`.  Se pueden indistintamente, pero `_stricmp` es el estándar preferido.  
  
 La función `_strcmpi`es equivalente a `_stricmp`y se proporciona por razones de compatibilidad con versiones anteriores.  
  
 Dado que `_stricmp` realiza comparaciones de minúsculas, podría producir un comportamiento inesperado.  
  
 Para ilustrar en qué casos la conversión de mayúsculas y minúsculas por parte de `_stricmp` afecta al resultado de una comparación, supongamos que se tienen las cadenas JOHNSTON y JOHN\_HENRY.  La cadena JOHN\_HENRY se considera menor que JOHNSTON porque “\_” tiene un valor ASCII menor que una S minúscula.  De hecho, cualquier carácter que tenga un valor ASCII entre 91 y 96 se considera menor que cualquier letra.  
  
 Si se usa la función [strcmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md) en lugar de `_stricmp`, JOHN\_HENRY será mayor que JOHNSTON.  
  
 `_wcsicmp` y `_mbsicmp` son versiones de caracteres anchos y multibyte de `_stricmp`.  Los argumentos y el valor devuelto de `_wcsicmp` son cadenas de caracteres anchos; los de `_mbsicmp` son cadenas de caracteres multibyte.  `_mbsicmp` reconoce secuencias de caracteres multibyte según la página actual de códigos multibyte y devuelve `_NLSCMPERROR` cuando se produce un error.  Para obtener más información, vea [Páginas de códigos](../../c-runtime-library/code-pages.md).  Estas tres funciones se comportan exactamente igual.  
  
 `_wcsicmp` y `wcscmp` se comportan exactamente igual, salvo que `wcscmp` no convierte los argumentos en minúsculas antes de compararlos.  `_mbsicmp` y `_mbscmp` se comportan exactamente igual, salvo que `_mbscmp` no convierte los argumentos en minúsculas antes de compararlos.  
  
 Debe llamar a [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para que `_wcsicmp` funcione con los caracteres de Latino 1.  La configuración regional de C está activada de forma predeterminada, de modo que, por ejemplo, ä no se considera igual a Ä.  Llame a `setlocale` con cualquier configuración regional distinta de la configuración regional de C antes de llamar a `_wcsicmp`.  En el ejemplo siguiente se muestra cómo la configuración regional afecta a `_wcsicmp`:  
  
```  
// crt_stricmp_locale.c  
#include <string.h>  
#include <stdio.h>  
#include <locale.h>  
  
int main() {  
   setlocale(LC_ALL,"C");   // in effect by default  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare fails  
   setlocale(LC_ALL,"");  
   printf("\n%d",_wcsicmp(L"ä", L"Ä"));   // compare succeeds  
}  
```  
  
 Una alternativa es llamar a [\_create\_locale, \_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md) y pasar el objeto de configuración regional devuelto a `_wcsicmp_l` como parámetro.  
  
 Todas estas funciones validan sus parámetros.  Si `string1` o `string2` son punteros nulos, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `_NLSCMPERROR` y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsicmp`|`_stricmp`|`_mbsicmp`|`_wcsicmp`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_stricmp`, `_stricmp_l`|\<string.h\>|  
|`_wcsicmp`, `_wcsicmp_l`|\<string.h\> o \<wchar.h\>|  
|`_mbsicmp`, `_mbsicmp_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_stricmp.c  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
char string1[] = "The quick brown dog jumps over the lazy fox";  
char string2[] = "The QUICK brown dog jumps over the lazy fox";  
  
int main( void )  
{  
   char tmp[20];  
   int result;  
  
   // Case sensitive  
   printf( "Compare strings:\n   %s\n   %s\n\n", string1, string2 );  
   result = strcmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   strcmp:   String 1 is %s string 2\n", tmp );  
  
   // Case insensitive (could use equivalent _stricmp)  
   result = _stricmp( string1, string2 );  
   if( result > 0 )  
      strcpy_s( tmp, _countof(tmp), "greater than" );  
   else if( result < 0 )  
      strcpy_s( tmp, _countof(tmp), "less than" );  
   else  
      strcpy_s( tmp, _countof(tmp), "equal to" );  
   printf( "   _stricmp:  String 1 is %s string 2\n", tmp );  
}  
```  
  
  **Cadenas de la comparación:**  
 **The quick brown dog jumps over the lazy fox**  
 **The QUICK brown dog jumps over the lazy fox**  
 **strcmp:   La cadena 1 es mayor que la cadena 2**  
 **\_stricmp:  La cadena 1 es igual a la cadena 2**   
## Equivalente en .NET Framework  
 [System::String::Compare](https://msdn.microsoft.com/en-us/library/system.string.compare.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [\_memicmp, \_memicmp\_l](../../c-runtime-library/reference/memicmp-memicmp-l.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strcoll \(Funciones\)](../../c-runtime-library/strcoll-functions.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [\_strset, \_strset\_l, \_wcsset, \_wcsset\_l, \_mbsset, \_mbsset\_l](../../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)