---
title: "_mbsnbcat_s, _mbsnbcat_s_l | Microsoft Docs"
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
  - "_mbsnbcat_s_l"
  - "_mbsnbcat_s"
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
  - "_mbsnbcat_s"
  - "mbsnbcat_s"
  - "_mbsnbcat_s_l"
  - "mbsnbcat_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnbcat_s (función)"
  - "_mbsnbcat_s_l (función)"
  - "_tcsncat (función)"
  - "_tcsncat_s_l (función)"
  - "mbsnbcat_s (función)"
  - "mbsnbcat_s_l (función)"
  - "tcsncat (función)"
  - "tcsncat_s_l (función)"
ms.assetid: 2c9e9be7-d979-4a54-8ada-23428b6648a9
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbsnbcat_s, _mbsnbcat_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Anexa a una cadena de caracteres multibyte, como máximo, los primeros bytes `n` de otra cadena de caracteres multibyte.  Se trata de versiones de [\_mbsnbcat, \_mbsnbcat\_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md) que tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  Para más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _mbsnbcat_s(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count   
);  
errno_t _mbsnbcat_s_l(  
   unsigned char *dest,  
   size_t sizeInBytes,  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _mbsnbcat_s(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbsnbcat_s_l(  
   unsigned char (&dest)[size],  
   const unsigned char *src,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `dest`  
 Cadena de destino de caracteres multibyte terminada en NULL.  
  
 `sizeInBytes`  
 Tamaño del búfer `dest` en bytes.  
  
 `src`  
 Cadena de origen de caracteres multibyte terminada en NULL.  
  
 `Count`  
 Número de bytes de `src` que se van a anexar a `dest`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cero si es correcto; en caso contrario, código de error.  
  
### Condiciones de error  
  
|`Dest`|`sizeInBytes`|`src`|Valor devuelto|  
|------------|-------------------|-----------|--------------------|  
|`NULL`|cualquiera|cualquiera|`EINVAL`|  
|Cualquiera|\<\= 0|cualquiera|`EINVAL`|  
|Cualquiera|cualquiera|`NULL`|`EINVAL`|  
  
 Si se produce alguna de las condiciones de error, la función genera un error de parámetro no válido, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si se controla el error, la función devuelve `EINVAL` y establece `errno` en `EINVAL`.  
  
## Comentarios  
 La función `_mbsnbcat_s` anexa a `dest`, como máximo, los primeros bytes `count` de `src`.  Si el byte que precede inmediatamente al carácter nulo en `dest` es un byte inicial, lo sobrescribe el byte inicial de `src`.  De lo contrario, el byte inicial de `src` sobrescribe el carácter nulo de terminación de `dest`.  Si hay un byte nulo en `src` antes de que se anexen `count` bytes, `_mbsnbcat_s` anexa todos los bytes de `src`, hasta el carácter nulo.  Si `count` es mayor que la longitud de `src`, se usa la longitud de `src` en lugar de `count`.  La cadena resultante se termina con un carácter nulo.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones son idénticas, salvo que las que no tienen el sufijo `_l` usan la configuración regional actual y las que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa.  Para obtener más información, consulte [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden inferir automáticamente la longitud de búfer, lo que elimina la necesidad de especificar un argumento de tamaño, y pueden usar automáticamente funciones más recientes y seguras para reemplazar las funciones anteriores no seguras.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsncat`|[strncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|`_mbsnbcat_s`|[wcsncat](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)|  
|`_tcsncat_s_l`|`_strncat_s_l`|`_mbsnbcat_s_l`|`_wcsncat_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mbsnbcat_s`|\<mbstring.h\>|  
|`_mbsnbcat_s_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_mbsnbcmp, \_mbsnbcmp\_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [\_strncnt, \_wcsncnt, \_mbsnbcnt, \_mbsnbcnt\_l, \_mbsnccnt, \_mbsnccnt\_l](../../c-runtime-library/reference/strncnt-wcsncnt-mbsnbcnt-mbsnbcnt-l-mbsnccnt-mbsnccnt-l.md)   
 [\_mbsnbcpy, \_mbsnbcpy\_l](../../c-runtime-library/reference/mbsnbcpy-mbsnbcpy-l.md)   
 [\_mbsnbcpy\_s, \_mbsnbcpy\_s\_l](../../c-runtime-library/reference/mbsnbcpy-s-mbsnbcpy-s-l.md)   
 [\_mbsnbset, \_mbsnbset\_l](../../c-runtime-library/reference/mbsnbset-mbsnbset-l.md)   
 [strncat, \_strncat\_l, wcsncat, \_wcsncat\_l, \_mbsncat, \_mbsncat\_l](../../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)   
 [strncat\_s, \_strncat\_s\_l, wcsncat\_s, \_wcsncat\_s\_l, \_mbsncat\_s, \_mbsncat\_s\_l](../../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)