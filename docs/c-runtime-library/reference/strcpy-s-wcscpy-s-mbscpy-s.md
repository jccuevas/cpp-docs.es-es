---
title: "strcpy_s, wcscpy_s, _mbscpy_s | Microsoft Docs"
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
  - "wcscpy_s"
  - "_mbscpy_s"
  - "strcpy_s"
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
  - "strcpy_s"
  - "_mbscpy_s"
  - "_tcscpy_s"
  - "wcscpy_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "strcpy_s (función)"
  - "_tcscpy_s (función)"
  - "_mbscpy_s (función)"
  - "copiar cadenas"
  - "copia de cadenas [C++]"
  - "tcscpy_s (función)"
  - "wcscpy_s (función)"
ms.assetid: 611326f3-7929-4a5d-a465-a4683af3b053
caps.latest.revision: 41
caps.handback.revision: 41
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcpy_s, wcscpy_s, _mbscpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copia una cadena. Estas versiones de [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbscpy_s` no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t strcpy_s(  
   char *strDestination,  
   size_t numberOfElements,  
   const char *strSource   
);  
errno_t wcscpy_s(  
   wchar_t *strDestination,  
   size_t numberOfElements,  
   const wchar_t *strSource   
);  
errno_t _mbscpy_s(  
   unsigned char *strDestination,  
   size_t numberOfElements,  
   const unsigned char *strSource   
);  
template <size_t size>  
errno_t strcpy_s(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
errno_t wcscpy_s(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
errno_t _mbscpy_s(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### Parámetros  
 `strDestination`  
 Ubicación del búfer de cadena de destino.  
  
 `numberOfElements`  
 Tamaño del búfer de cadena de destino en unidades `char` para las funciones estrechas y multibyte, y unidades `wchar_t` para las funciones anchas.  
  
 `strSource`  
 Búfer de cadena de origen terminada en NULL.  
  
## Valor devuelto  
 Cero si es correcto; en caso contrario, error.  
  
### Condiciones de error  
  
|`strDestination`|`numberOfElements`|`strSource`|Valor devuelto|Contenido de `strDestination`|  
|----------------------|------------------------|-----------------|--------------------|-----------------------------------|  
|`NULL`|any|any|`EINVAL`|no modificado|  
|any|any|`NULL`|`EINVAL`|`strDestination`\[0\] se establece en 0|  
|cualquiera|0, o demasiado pequeño|any|`ERANGE`|`strDestination`\[0\] se establece en 0|  
  
## Comentarios  
 La función `strcpy_s` copia el contenido de la dirección de `strSource`, incluido el carácter nulo de terminación, en la ubicación especificada por `strDestination`. La cadena de destino debe ser lo suficientemente grande como para contener la cadena de origen y su carácter nulo de terminación. El comportamiento de `strcpy_s` no se define si las cadenas de origen y de destino se superponen.  
  
 `wcscpy_s` es la versión con caracteres anchos de `strcpy_s` y `_mbscpy_s` es la versión de caracteres multibyte. Los argumentos y el valor devuelto de `wcscpy_s` son cadenas de caracteres anchos; los de `_mbscpy_s` son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.  
  
 Si `strDestination` o `strSource` es un puntero nulo, o si la cadena de destino es demasiado pequeña, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EINVAL` y establecen `errno` en `EINVAL` cuando `strDestination` o `strSource` es un puntero nulo, y devuelven `ERANGE` y establecen `errno` en `ERANGE` cuando la cadena de destino es demasiado pequeña.  
  
 Si la ejecución finaliza correctamente, la cadena de destino siempre termina en null.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla —que pueden realizar automáticamente una inferencia de la longitud de búfer para eliminar la necesidad de especificar un argumento de tamaño— y pueden reemplazar automáticamente funciones anteriores no seguras por sus homólogos seguros más recientes. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFE. Para deshabilitar este comportamiento, utilice [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcscpy_s`|`strcpy_s`|`_mbscpy_s`|`wcscpy_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strcpy_s`|\<string.h\>|  
|`wcscpy_s`|\<string.h\> o \<wchar.h\>|  
|`_mbscpy_s`|\<mbstring.h\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strcpy_s.cpp  
// This program uses strcpy_s and strcat_s  
// to build a phrase.  
//  
  
#include <string.h>  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
   char string[80];  
   // using template versions of strcpy_s and strcat_s:  
   strcpy_s( string, "Hello world from " );  
   strcat_s( string, "strcpy_s " );  
   strcat_s( string, "and " );  
   // of course we can supply the size explicitly if we want to:  
   strcat_s( string, _countof(string), "strcat_s!" );  
  
   printf( "String = %s\n", string );  
}  
```  
  
```Output  
String = Hello world from strcpy_s and strcat_s!  
```  
  
## Equivalente en .NET Framework  
 [System::String::Copy](https://msdn.microsoft.com/en-us/library/system.string.copy.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)