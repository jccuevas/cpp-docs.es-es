---
title: "_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_strupr_s"
  - "_strupr_s_l"
  - "_mbsupr_s"
  - "_wcsupr_s_l"
  - "_mbsupr_s_l"
  - "_wcsupr_s"
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
  - "strupr_s"
  - "mbsupr_s"
  - "wcsupr_s"
  - "_mbsupr_s_l"
  - "mbsupr_s_l"
  - "wcsupr_s_l"
  - "_wcsupr_s"
  - "_tcsupr_s_l"
  - "_mbsupr_s"
  - "_tcsupr_s"
  - "strupr_s_l"
  - "_wcsupr_s_l"
  - "_strupr_s"
  - "_strupr_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbsupr_s (función)"
  - "_mbsupr_s_l (función)"
  - "_strupr_s (función)"
  - "_strupr_s_l (función)"
  - "_tcsupr_s (función)"
  - "_tcsupr_s_l (función)"
  - "_wcsupr_s (función)"
  - "_wcsupr_s_l (función)"
  - "convertir mayúsculas y minúsculas, CRT (funciones)"
  - "mbsupr_s (función)"
  - "mbsupr_s_l (función)"
  - "conversión de cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], mayúsculas y minúsculas"
  - "cadenas [C++], convertir mayúsculas y minúsculas"
  - "strupr_s (función)"
  - "strupr_s_l (función)"
  - "tcsupr_s (función)"
  - "tcsupr_s_l (función)"
  - "mayúsculas, convertir cadenas en"
  - "wcsupr_s (función)"
  - "wcsupr_s_l (función)"
ms.assetid: 82d3a273-9f6f-4a26-9560-919d891e4581
caps.latest.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 30
---
# _strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Pone una cadena en mayúsculas usando la configuración regional actual o la configuración regional especificada que se pasa.  Estas versiones de [\_strupr, \_strupr\_l, \_mbsupr, \_mbsupr\_l, \_wcsupr\_l, \_wcsupr](../../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
> [!IMPORTANT]
>  `_mbsupr_s` y `_mbsupr_s_l` no se pueden usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
errno_t _strupr_s(  
   char *str,  
   size_t numberOfElements  
);  
errno_t _wcsupr_s(  
   wchar_t * str,  
   size_t numberOfElements  
);  
errno_t _strupr_s_l(  
   char * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _wcsupr_s_l(  
   wchar_t * str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _mbsupr_s(  
   unsigned char *str,  
   size_t numberOfElements  
);  
errno_t _mbsupr_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _strupr_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _strupr_s_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _wcsupr_s_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _mbsupr_s_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a poner en mayúsculas.  
  
 `numberOfElements`  
 Tamaño del búfer.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error de valor distinto de cero si se produce un error.  
  
 Estas funciones validan sus parámetros.  Si `str` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  Si `numberOfElements` es menor que la longitud de la cadena, las funciones devuelven `ERANGE` y establecen `errno` en `ERANGE`.  
  
## Comentarios  
 La función `_strupr_s` convierte, en su sitio, cada minúscula de `str` en mayúscula.  `_wcsupr_s` es la versión con caracteres anchos de `_strupr_s`.  `_mbsupr_s` es la versión de caracteres multibyte de `_strupr_s`.  
  
 El valor de la categoría `LC_CTYPE` de la configuración regional determina la conversión.  Otros caracteres no resultan afectados.  Para obtener más información sobre `LC_CTYPE`, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 Las versiones de depuración de estas funciones rellenan primero el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcsupr_s`|`_strupr_s`|`_mbsupr_s`|`_wcsupr_s`|  
|`_tcsupr_s_l`|`_strupr_s_l`|`_mbsupr_s_l`|`_wcsupr_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strupr_s`, `_strupr_s_l`|\<string.h\>|  
|`_wcsupr_s`, `_wcsupr_s_l`, `_mbsupr_s`, `_mbsupr_s_l`|\<string.h\> o \<wchar.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Consulte el ejemplo de [\_strlwr\_s, \_strlwr\_s\_l, \_mbslwr\_s, \_mbslwr\_s\_l, \_wcslwr\_s, \_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md).  
  
## Equivalente en .NET Framework  
 [System::String::ToUpper](https://msdn.microsoft.com/en-us/library/system.string.toupper.aspx)  
  
## Vea también  
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [\_strlwr\_s, \_strlwr\_s\_l, \_mbslwr\_s, \_mbslwr\_s\_l, \_wcslwr\_s, \_wcslwr\_s\_l](../../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)