---
title: "_strdup, _wcsdup, _mbsdup | Microsoft Docs"
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
  - "_strdup"
  - "_mbsdup"
  - "_wcsdup"
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
  - "_tcsdup"
  - "mbsdup"
  - "_mbsdup"
  - "_strdup"
  - "_ftcsdup"
  - "_wcsdup"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wcsdup (función)"
  - "ftcsdup (función)"
  - "_ftcsdup (función)"
  - "mbsdup (función)"
  - "strdup (función)"
  - "_strdup (función)"
  - "_wcsdup (función)"
  - "copiar cadenas"
  - "duplicar cadenas"
  - "copia de cadenas [C++]"
  - "_mbsdup (función)"
  - "duplicar de cadenas [C++]"
  - "tcsdup (función)"
  - "_tcsdup (función)"
ms.assetid: 8604f8bb-95e9-45d3-93ef-20397ebf247a
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strdup, _wcsdup, _mbsdup
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Duplica cadenas.  
  
> [!IMPORTANT]
>  `_mbsdup` no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]. Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *_strdup(  
   const char *strSource   
);  
wchar_t *_wcsdup(  
   const wchar_t *strSource   
);  
unsigned char *_mbsdup(  
   const unsigned char *strSource   
);  
```  
  
#### Parámetros  
 `strSource`  
 Cadena de origen terminada en NULL.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la ubicación de almacenamiento para la cadena copiada o `NULL` si no se puede asignar almacenamiento.  
  
## Comentarios  
 La función `_strdup` llama a [malloc](../../c-runtime-library/reference/malloc.md) para asignar espacio de almacenamiento para una copia de `strSource` y, a continuación, copia `strSource` en el espacio asignado.  
  
 `_wcsdup` y `_mbsdup` son versiones de caracteres anchos y multibyte de `_strdup`. Los argumentos y el valor devuelto de `_wcsdup` son cadenas de caracteres anchos; los de `_mbsdup` son cadenas de caracteres multibyte. Estas tres funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsdup`|`_strdup`|`_mbsdup`|`_wcsdup`|  
  
 Dado que `_strdup` llama a `malloc` para asignar espacio de almacenamiento para la copia de `strSource`, siempre es recomendable liberar esta memoria mediante una llamada a la rutina [free](../../c-runtime-library/reference/free.md) del puntero devuelto por la llamada a `_strdup`.  
  
 Si `_DEBUG` y `_CRTDBG_MAP_ALLOC` están definidos, `_strdup` y `_wcsdup` se reemplazan por llamadas a `_strdup_dbg` y `_wcsdup_dbg` para admitir asignaciones de memoria de depuración. Para obtener más información, vea [\_strdup\_dbg, \_wcsdup\_dbg](../../c-runtime-library/reference/strdup-dbg-wcsdup-dbg.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strdup`|\<string.h\>|  
|`_wcsdup`|\<string.h\> o \<wchar.h\>|  
|`_mbsdup`|\<mbstring.h\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strdup.c  
  
#include <string.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[] = "This is the buffer text";  
   char *newstring;  
   printf( "Original: %s\n", buffer );  
   newstring = _strdup( buffer );  
   printf( "Copy:     %s\n", newstring );  
   free( newstring );  
}  
```  
  
```Output  
Original: este es el texto de búfer Copia: este es el texto de búfer  
```  
  
## Equivalente en .NET Framework  
 [System::String::Clone](https://msdn.microsoft.com/en-us/library/system.string.clone.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcat, wcscat, \_mbscat](../../c-runtime-library/reference/strcat-wcscat-mbscat.md)   
 [strcmp, wcscmp, \_mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)