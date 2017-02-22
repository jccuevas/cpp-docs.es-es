---
title: "vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vswprintf_s_l"
  - "vsprintf_s"
  - "vswprintf_s"
  - "_vsprintf_s_l"
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
apitype: "DLLExport"
f1_keywords: 
  - "vswprintf_s"
  - "vsprintf_s"
  - "_vstprintf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vstprintf_s_l (función)"
  - "vsprintf_s_l (función)"
  - "_vstprintf_s (función)"
  - "vswprintf_s (función)"
  - "vstprintf_s (función)"
  - "vstprintf_s_l (función)"
  - "vswprintf_s_l (función)"
  - "vsprintf_s (función)"
  - "_vsprintf_s_l (función)"
  - "texto con formato [C++]"
  - "_vswprintf_s_l (función)"
ms.assetid: 60e90518-57f0-4f1b-b732-f62a69702833
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# vsprintf_s, _vsprintf_s_l, vswprintf_s, _vswprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe un resultado con formato mediante un puntero a una lista de argumentos.  Estas versiones de [vsprintf, \_vsprintf\_l, vswprintf, \_vswprintf\_l, \_\_vswprintf\_l](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int vsprintf_s(  
   char *buffer,  
   size_t numberOfElements,  
   const char *format,  
   va_list argptr   
);   
int _vsprintf_s_l(  
   char *buffer,  
   size_t numberOfElements,  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);   
int vswprintf_s(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *format,  
   va_list argptr   
);  
int _vswprintf_s_l(  
   wchar_t *buffer,  
   size_t numberOfElements,  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
template <size_t size>  
int vsprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   va_list argptr   
); // C++ only  
template <size_t size>  
int vswprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   va_list argptr   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
 `numberOfElements`  
 Tamaño de `buffer` en caracteres.  
  
 `format`  
 Especificación de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `vsprintf_s` y `vswprintf_s` devuelven el número de caracteres escritos, sin incluir el carácter de terminación nulo, o un valor negativo si se produce un error de salida.  Si `buffer` o `format` es un puntero NULL, si el número es cero, o si la cadena de formato contiene caracteres de formato no válidos, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones toma un puntero a una lista de argumentos y, a continuación, aplica formato a los datos determinados y los escribe en la memoria a la que señala `buffer`.  
  
 `vswprintf_s` se ajusta a ISO C estándar para `vswprintf`, que requiere el segundo parámetro, `count`, de `size_t`escrito.  
  
 Estas funciones se diferencian de las versiones de no Secure sólo en que las versiones seguras admiten parámetros posicionales.  Para obtener más información, vea [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vstprintf_s`|`vsprintf_s`|`vsprintf_s`|`vswprintf_s`|  
|`_vstprintf_s_l`|`_vsprintf_s_l`|`_vsprintf_s_l`|`_vswprintf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`vsprintf_s`, `_vsprintf_s_l`|\<stdio.h\> y \<stdarg.h\>|\<varargs.h\>\*|  
|`vswprintf_s`, `_vswprintf_s_l`|\<stdio.h\> o \<wchar.h\>, y \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* Necesario para la compatibilidad con UNIX V.  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_vsprintf_s.c  
// This program uses vsprintf_s to write to a buffer.  
// The size of the buffer is determined by _vscprintf.  
  
#include <stdlib.h>  
#include <stdarg.h>  
  
void test( char * format, ... )  
{  
   va_list args;  
   int len;  
   char * buffer;  
  
   va_start( args, format );  
   len = _vscprintf( format, args ) // _vscprintf doesn't count  
                               + 1; // terminating '\0'  
   buffer = malloc( len * sizeof(char) );  
   vsprintf_s( buffer, len, format, args );  
   puts( buffer );  
   free( buffer );  
}  
  
int main( void )  
{  
   test( "%d %c %d", 123, '<', 456 );  
   test( "%s", "This is a string" );  
}  
```  
  
  **123 \< 456**  
**This is a string**   
## Equivalente en .NET Framework  
 [System::String::Format](https://msdn.microsoft.com/en-us/library/system.string.format.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg, va\_copy, va\_end, va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)