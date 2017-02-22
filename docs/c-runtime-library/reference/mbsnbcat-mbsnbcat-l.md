---
title: "_mbsnbcat, _mbsnbcat_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbsnbcat_l"
  - "_mbsnbcat"
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
  - "mbsnbcat"
  - "mbsnbcat_l"
  - "_mbsnbcat"
  - "_mbsnbcat_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsnbcat (función)"
  - "_mbsnbcat_l (función)"
  - "_tcsncat (función)"
  - "_tcsncat_l (función)"
  - "mbsnbcat (función)"
  - "mbsnbcat_l (función)"
  - "tcsncat (función)"
  - "tcsncat_l (función)"
ms.assetid: aa0f1d30-0ddd-48d1-88eb-c6884b20fd91
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _mbsnbcat, _mbsnbcat_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Anexa, como máximo, los primeros `n` bytes de una cadena de caracteres multibyte en otra.  Hay disponibles versiones más seguras de estas funciones; vea [\_mbsnbcat\_s, \_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
unsigned char *_mbsnbcat(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count   
);  
unsigned char *_mbsnbcat_l(  
   unsigned char *dest,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
unsigned char *_mbsnbcat(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
unsigned char *_mbsnbcat_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `dest`  
 Cadena de destino de caracteres multibyte terminada en NULL.  
  
 `src`  
 Cadena de origen de caracteres multibyte terminada en NULL.  
  
 `count`  
 Número de bytes de `src` que se van a anexar a `dest`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_mbsnbcat` devuelve un puntero a la cadena de destino.  No se reserva ningún valor devuelto para indicar un error.  
  
## Comentarios  
 La función `_mbsnbcat` anexa, como máximo, los primeros `count` bytes de `src` a `dest`.  Si el byte que precede inmediatamente al carácter nulo en `dest` es un byte inicial, byte inicial de `src` sobrescribe este byte inicial.  De lo contrario, el byte inicial de `src` sobrescribe el carácter nulo de terminación de `dest`.  Si hay un byte null en `src` antes de que se anexen `count` bytes, \_`mbsnbcat` anexa todos los bytes de `src`, hasta el carácter nulo.  Si `count` es mayor que la longitud de `src`, se usa la longitud de `src` en lugar de `count`.  La cadena resultante se termina con un carácter nulo.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  La versión `_mbsnbcat` de esta función usa la configuración regional actual de su comportamiento dependiente de la configuración regional; la versión `_mbsnbcat_l` es idéntica, salvo que usa el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 **Nota de seguridad** Use una cadena terminada en un valor nulo.  El tamaño de la cadena terminada en un valor nulo no debe ser mayor que el del búfer de destino.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Si `dest` o `src` es `NULL`, la función generará un error de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si se controla el error, la función devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_l`|`_strncat_l`|`_mbsnbcat_l`|`_wcsncat_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbcat`|\<mbstring.h\>|  
|`_mbsnbcat_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcmp, \_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt, \_wcsncnt, \_mbsnbcnt, \_mbsnbcnt\_l, \_mbsnccnt, \_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbcpy, \_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [\_mbsnbicmp, \_mbsnbicmp\_l](../../c-runtime-library/reference/mbsnbicmp-mbsnbicmp-l.md)   
 [\_mbsnbset, \_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [\_mbsnbcat\_s, \_mbsnbcat\_s\_l](../../c-runtime-library/reference/mbsnbcat-s-mbsnbcat-s-l.md)