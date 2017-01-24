---
title: "_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l | Microsoft Docs"
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
  - "_strlwr_l"
  - "_strlwr"
  - "_wcslwr_l"
  - "_mbslwr_l"
  - "_wcslwr"
  - "_mbslwr"
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
  - "_strlwr"
  - "wcslwr_l"
  - "_ftcslwr"
  - "mbslwr_l"
  - "_mbslwr"
  - "_wcslwr"
  - "strlwr_l"
  - "_tcslwr"
  - "mbslwr"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcslwr (función)"
  - "_mbslwr (función)"
  - "_mbslwr_l (función)"
  - "_strlwr (función)"
  - "_strlwr_l (función)"
  - "_tcslwr (función)"
  - "_tcslwr_l (función)"
  - "_wcslwr (función)"
  - "_wcslwr_l (función)"
  - "mayúsculas y minúsculas, convertir"
  - "convertir mayúsculas y minúsculas"
  - "convertir mayúsculas y minúsculas, CRT (funciones)"
  - "ftcslwr (función)"
  - "mbslwr (función)"
  - "mbslwr_l (función)"
  - "conversión de cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], convertir mayúsculas y minúsculas"
  - "strlwr_l (función)"
  - "tcslwr (función)"
  - "tcslwr_l (función)"
  - "wcslwr_l (función)"
ms.assetid: d279181d-2e7d-401f-ab44-6e7c2786a046
caps.latest.revision: 36
caps.handback.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cambia la cadena a minúsculas.  Hay disponibles versiones más seguras de estas funciones; vea [\_strlwr\_s, \_strlwr\_s\_l, \_mbslwr\_s, \_mbslwr\_s\_l, \_wcslwr\_s, \_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).  
  
> [!IMPORTANT]
>  `_mbslwr` y `_mbslwr_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strlwr(  
   char * str  
);  
wchar_t *_wcslwr(  
   wchar_t * str  
);  
unsigned char *_mbslwr(  
   unsigned char * str  
);  
char *_strlwr_l(  
   char * str,  
   _locale_t locale  
);  
wchar_t *_wcslwr_l(  
   wchar_t * str,  
   _locale_t locale  
);  
unsigned char *_mbslwr_l(  
   unsigned char * str,  
   _locale_t locale   
);  
template <size_t size>  
char *_strlwr(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
char *_strlwr_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
wchar_t *_wcslwr_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
unsigned char *_mbslwr_l(  
   unsigned char (&str)[size],  
   _locale_t locale   
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena terminada en NULL que se va a cambiar a minúsculas.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la cadena convertida.  Dado que la modificación se hace en contexto, el puntero devuelto es el mismo que el puntero que se pasa como argumento de entrada.  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `_strlwr`  cambia todas las mayúsculas de `str` a minúsculas, según lo determina el valor de la categoría `LC_CTYPE` de la configuración regional.  Otros caracteres no resultan afectados.  Para obtener más información sobre `LC_CTYPE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l`  son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Las funciones `_wcslwr` y `_mbslwr` son versiones de caracteres anchos y multibyte de `_strlwr`.  El argumento y el valor devuelto de `_wcslwr` son cadenas de caracteres anchos; los de `_mbslwr` son cadenas de caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
 Si `str` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven la cadena original y establecen `errno` en `EINVAL`.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcslwr`|`_strlwr`|`_mbslwr`|`_wcslwr`|  
|`_tcslwr_l`|`_strlwr_l`|`_mbslwr_l`|`_wcslwr_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strlwr`, `_strlwr_l`|\<string.h\>|  
|`_wcslwr`, `_wcslwr_l`|\<string.h\> o \<wchar.h\>|  
|`_mbslwr`, `_mbslwr_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strlwr.c  
// compile with: /W3  
// This program uses _strlwr and _strupr to create  
// uppercase and lowercase copies of a mixed-case string.  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char string[100] = "The String to End All Strings!";  
   char * copy1 = _strdup( string ); // make two copies  
   char * copy2 = _strdup( string );  
  
   _strlwr( copy1 ); // C4996  
   // Note: _strlwr is deprecated; consider using _strlwr_s instead  
   _strupr( copy2 ); // C4996  
   // Note: _strupr is deprecated; consider using _strupr_s instead  
  
   printf( "Mixed: %s\n", string );  
   printf( "Lower: %s\n", copy1 );  
   printf( "Upper: %s\n", copy2 );  
  
   free( copy1 );  
   free( copy2 );  
}  
```  
  
  **Mixed: The String to End All Strings\!**  
**Lower: the string to end all strings\!**  
**Upper: THE STRING TO END ALL STRINGS\!**   
## Equivalente en .NET Framework  
 [System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_strupr, \_strupr\_l, \_mbsupr, \_mbsupr\_l, \_wcsupr\_l, \_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md)