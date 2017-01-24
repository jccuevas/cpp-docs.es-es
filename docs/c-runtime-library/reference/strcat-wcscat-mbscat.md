---
title: "strcat, wcscat, _mbscat | Microsoft Docs"
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
  - "_mbscat"
  - "wcscat"
  - "strcat"
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
  - "_mbscat"
  - "_ftcscat"
  - "_tcscat"
  - "strcat"
  - "wcscat"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ftcscat (función)"
  - "_mbscat (función)"
  - "_tcscat (función)"
  - "anexar cadenas"
  - "concatenar cadenas"
  - "ftcscat (función)"
  - "mbscat (función)"
  - "strcat (función)"
  - "cadenas [C++], asociar"
  - "cadenas [C++], concatenar"
  - "tcscat (función)"
  - "wcscat (función)"
ms.assetid: c89c4ef1-817a-44ff-a229-fe22d06ba78a
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strcat, wcscat, _mbscat
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Anexa una cadena.  Hay disponibles versiones más seguras de estas funciones; vea [strcat\_s, wcscat\_s, \_mbscat\_s](../../c-runtime-library/reference/strcat-s-wcscat-s-mbscat-s.md).  
  
> [!IMPORTANT]
>  `_mbscat_s` no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
char *strcat(  
   char *strDestination,  
   const char *strSource   
);  
wchar_t *wcscat(  
   wchar_t *strDestination,  
   const wchar_t *strSource   
);  
unsigned char *_mbscat(  
   unsigned char *strDestination,  
   const unsigned char *strSource   
);  
template <size_t size>  
char *strcat(  
   char (&strDestination)[size],  
   const char *strSource   
); // C++ only  
template <size_t size>  
wchar_t *wcscat(  
   wchar_t (&strDestination)[size],  
   const wchar_t *strSource   
); // C++ only  
template <size_t size>  
unsigned char *_mbscat(  
   unsigned char (&strDestination)[size],  
   const unsigned char *strSource   
); // C++ only  
```  
  
#### Parámetros  
 `strDestination`  
 Cadena de destino terminada en NULL.  
  
 `strSource`  
 Cadena de origen terminada en NULL.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve la cadena de destino \(`strDestination`\).  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `strcat` anexa `strSource` a `strDestination` y termina la cadena resultante con un carácter nulo.  El carácter inicial de `strSource` sobrescribe el carácter nulo de terminación de `strDestination`.  El comportamiento de `strcat` no se define si las cadenas de origen y de destino se superponen.  
  
> [!IMPORTANT]
>  Dado que `strcat` no comprueba si hay espacio suficiente en `strDestination` antes de anexar `strSource`, podría dar lugar a saturaciones del búfer.  Considere la posibilidad de usar [strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md) en su lugar.  
  
 `wcscat` y `_mbscat` son versiones de caracteres anchos y multibyte de `strcat`.  Los argumentos y el valor devuelto de `wcscat` son cadenas de caracteres anchos; los de `_mbscat` son cadenas de caracteres multibyte.  Estas tres funciones se comportan exactamente igual.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcscat`|`strcat`|`_mbscat`|`wcscat`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strcat`|\<string.h\>|  
|`wcscat`|\<string.h\> o \<wchar.h\>|  
|`_mbscat`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md).  
  
## Equivalente en .NET Framework  
 [System::String::Concat](https://msdn.microsoft.com/en-us/library/system.string.concat.aspx)  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncmp, wcsncmp, \_mbsncmp, \_mbsncmp\_l](../../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [\_strnicmp, \_wcsnicmp, \_mbsnicmp, \_strnicmp\_l, \_wcsnicmp\_l, \_mbsnicmp\_l](../../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)   
 [strrchr, wcsrchr, \_mbsrchr, \_mbsrchr\_l](../../c-runtime-library/reference/strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)   
 [strspn, wcsspn, \_mbsspn, \_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)