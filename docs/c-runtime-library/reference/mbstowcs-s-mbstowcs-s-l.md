---
title: "mbstowcs_s, _mbstowcs_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_mbstowcs_s_l"
  - "mbstowcs_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstowcs_s_l (función)"
  - "mbstowcs_s (función)"
  - "mbstowcs_s_l (función)"
ms.assetid: 2fbda953-6918-498f-b440-3e7b21ed65a4
caps.latest.revision: 31
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 31
---
# mbstowcs_s, _mbstowcs_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una secuencia de caracteres multibyte en una secuencia correspondiente de caracteres anchos.  Versiones de [mbstowcs, \_mbstowcs\_l](../../c-runtime-library/reference/mbstowcs-mbstowcs-l.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count   
);  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t *wcstr,  
   size_t sizeInWords,  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
);  
template <size_t size>  
errno_t mbstowcs_s(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count   
); // C++ only  
template <size_t size>  
errno_t _mbstowcs_s_l(  
   size_t *pReturnValue,  
   wchar_t (&wcstr)[size],  
   const char *mbstr,  
   size_t count,  
   _locale_t locale  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `pReturnValue`  
 El número de caracteres convertido.  
  
 \[out\] `wcstr`  
 La dirección de búfer para producir convirtió la cadena de caracteres anchos.  
  
 \[in\] `sizeInWords`  
 El tamaño del búfer de `wcstr` en palabras.  
  
 \[in\]`mbstr`  
 La dirección de una secuencia de null finalizó caracteres multibyte.  
  
 \[in\] `count`  
 El número máximo de caracteres anchos a almacenar en el búfer de `wcstr` , sin incluir la null final, o [\_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 \[in\] `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
|Condición de error|Valor devuelto y `errno`|  
|------------------------|------------------------------|  
|`wcstr` es `NULL` y `sizeInWords` \> 0|`EINVAL`|  
|El valor de `mbstr` es `NULL`.|`EINVAL`|  
|El búfer de destino es demasiado pequeño para contener la cadena convertida \(a menos que `count` es `_TRUNCATE`; vea las notas siguiente\)|`ERANGE`|  
|`wcstr` no es `NULL` y \=\= 0 de `sizeInWords`|`EINVAL`|  
  
 Si cualquiera de estas condiciones aparecen, la excepción no válida de parámetros se invoca como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, la función devuelve un código de error y establece `errno` como se indica en la tabla.  
  
## Comentarios  
 La función de `mbstowcs_s` convierte una cadena de caracteres multibyte indicada por `mbstr` en los caracteres anchos almacenados en el búfer indicada por `wcstr`.  La conversión continuará por cada carácter hasta que una de estas condiciones se cumple:  
  
-   Se encuentra un carácter null multibyte  
  
-   Se encuentra un carácter no válido multibyte  
  
-   El número de caracteres anchos almacenados en el búfer de `wcstr` es igual a `count`.  
  
 La cadena de destino siempre es terminada en null \(incluso en el caso de un error\).  
  
 Si `count` es el valor especial [\_TRUNCATE](../../c-runtime-library/truncate.md), después `mbstowcs_s` convierte tanto de la cadena que caben en el búfer de destino, mientras todavía deja el sitio para un carácter null final.  
  
 Si `mbstowcs_s` convierte correctamente la cadena de origen, coloca el tamaño en caracteres anchos de la cadena convertida, incluido el terminador nulo, en `*``pReturnValue` \( `pReturnValue` proporcionado no es `NULL`\).  Esto hace que incluso si el argumento de `wcstr` es `NULL` y proporciona una manera de determinar el tamaño de búfer requerido.  Tenga en cuenta que si `wcstr` es `NULL`, `count` se omite, y `sizeInWords` debe ser 0.  
  
 Si `mbstowcs_s` encuentra un carácter no válido multibyte, coloca 0 en `*``pReturnValue`, establece el búfer de destino en una cadena vacía, establece `errno` a `EILSEQ`, y devuelve `EILSEQ`.  
  
 Si las secuencias designadas por a `mbstr` y la superposición de `wcstr` , el comportamiento de `mbstowcs_s` no están definidas.  
  
> [!IMPORTANT]
>  Asegúrese de que `wcstr` y `mbstr` no se superpongan, y que `count` correctamente refleja el número de caracteres multibyte convertir.  
  
 `mbstowcs_s` utiliza la configuración regional actual para cualquier comportamiento configuración regional\-dependiente; `_mbstowcs_s_l` es idéntico pero utiliza la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`mbstowcs_s`|\<stdlib.h\>|  
|`_mbstowcs_s_l`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_mbclen, mblen, \_mblen\_l](../../c-runtime-library/reference/mbclen-mblen-mblen-l.md)   
 [mbtowc, \_mbtowc\_l](../../c-runtime-library/reference/mbtowc-mbtowc-l.md)   
 [wcstombs, \_wcstombs\_l](../../c-runtime-library/reference/wcstombs-wcstombs-l.md)   
 [wctomb, \_wctomb\_l](../../c-runtime-library/reference/wctomb-wctomb-l.md)