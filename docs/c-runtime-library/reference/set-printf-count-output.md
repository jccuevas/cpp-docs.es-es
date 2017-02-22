---
title: "_set_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_printf_count_output"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "set_printf_count_output"
  - "_set_printf_count_output"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "%n (formato)"
  - "_set_printf_count_output (función)"
  - "set_printf_count_output (función)"
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _set_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Compatibilidad de permisos o de deshabilitar la opción de formato de `%n` en [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\- la familia funciona.  
  
## Sintaxis  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### Parámetros  
 `enable`  
 Un valor distinto de cero para habilitar `%n` admite, 0 para deshabilitar la compatibilidad de `%n` .  
  
## Valor de propiedad y valor devuelto  
 El estado de la compatibilidad de `%n` antes de llamar a esta función: distinto de cero si la compatibilidad de `%n` está habilitado, 0 si se deshabilitó.  
  
## Comentarios  
 Por motivos de seguridad, compatibilidad con el especificador de formato de `%n` está deshabilitada de forma predeterminada en `printf` y todos sus variantes.  Si `%n` se encuentra en una especificación de formato de `printf` , el comportamiento predeterminado consiste en invocar el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  La llamada `_set_printf_count_output` con un argumento distinto producirá `printf`\- funciones de familia para interpretar `%n` como se describe en [printf \(Caracteres de campo de tipo\)](../../c-runtime-library/printf-type-field-characters.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_printf_count_output`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
## Resultados  
  
```  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## Equivalente de .NET Framework  
 No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [\_get\_printf\_count\_output](../../c-runtime-library/reference/get-printf-count-output.md)