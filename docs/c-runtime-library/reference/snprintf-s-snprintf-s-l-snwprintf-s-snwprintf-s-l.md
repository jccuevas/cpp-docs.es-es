---
title: "_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_snprintf_s"
  - "_snprintf_s_l"
  - "_snwprintf_s"
  - "_snwprintf_s_l"
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
  - "_snwprintf_s_l"
  - "_sntprintf_s_l"
  - "snprintf_s_l"
  - "_snprintf_s_l"
  - "_sntprintf_s"
  - "_snprintf_s"
  - "snprintf_s"
  - "_snwprintf_s"
  - "snwprintf_s_l"
  - "snwprintf_s"
  - "sntprintf_s"
  - "sntprintf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_snprintf_s (función)"
  - "_snprintf_s_l (función)"
  - "_sntprintf_s (función)"
  - "_sntprintf_s_l (función)"
  - "_snwprintf_s (función)"
  - "_snwprintf_s_l (función)"
  - "texto con formato [C++]"
  - "snprintf_s (función)"
  - "snprintf_s_l (función)"
  - "sntprintf_s (función)"
  - "sntprintf_s_l (función)"
  - "snwprintf_s (función)"
  - "snwprintf_s_l (función)"
ms.assetid: 9336ab86-13e5-4a29-a3cd-074adfee6891
caps.latest.revision: 32
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Escribe datos con formato en una cadena. Estas son versiones de [snprintf, \_snprintf, \_snprintf\_l, \_snwprintf, \_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int _snprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format [,  
   argument] ...   
);  
int _snprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _snwprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
);  
int _snwprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   size_t count,  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
template <size_t size>  
int _snprintf_s(  
   char (&buffer)[size],  
   size_t count,  
   const char *format [,  
   argument] ...   
); // C++ only  
template <size_t size>  
int _snwprintf_s(  
   wchar_t (&buffer)[size],  
   size_t count,  
   const wchar_t *format [,  
   argument] ...   
); // C++ only  
```  
  
#### Parámetros  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
 `sizeOfBuffer`  
 El tamaño de la ubicación de almacenamiento para la salida. El tamaño de `bytes` para `_snprintf_s` o tamaño en `words` para `_snwprintf_s`.  
  
 `Count`  
 Número máximo de caracteres que se va a almacenar, o [\_TRUNCATE](../../c-runtime-library/truncate.md).  
  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_snprintf_s` Devuelve el número de caracteres almacenados en `buffer`, sin contar el carácter nulo de terminación.`_snwprintf_s` devuelve el número de caracteres anchos almacenados en `buffer`, sin contar el carácter ancho final null.  
  
 Si supera el almacenamiento necesario para almacenar los datos y un valor null de terminación `sizeOfBuffer`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución continúa después del controlador de parámetros no válidos, estas funciones establecen `buffer` en una cadena vacía, establecen `errno` en `ERANGE` y devuelven \-1.  
  
 Si `buffer` o `format` es un puntero `NULL`, o si `count` es menor o igual que cero, se invoca el controlador de parámetros no válidos. Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven \-1.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 El `_snprintf_s` almacenes y formatos de la función `count` o menos caracteres en `buffer` y anexa un carácter nulo. Cada argumento \(si existe\) se convierte y sale según la especificación de formato correspondiente en `format`. El formato es coherente con el `printf` familia de funciones; vea [Sintaxis de especificación de formato: Funciones printf y wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md). Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 Si `count` es [\_TRUNCATE](../../c-runtime-library/truncate.md), a continuación, `_snprintf_s` escrituras como gran parte de la cadena como caben en `buffer` y dejan espacio para un carácter nulo. Si la cadena completa \(con valor nulo final\) cabe en `buffer`, a continuación, `_snprintf_s` devuelve el número de caracteres escrito \(sin incluir el carácter null\); en caso contrario, `_snprintf_s` devuelve \-1 para indicar que el truncamiento se produjo.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
 `_snwprintf_s` es una versión con caracteres anchos de `_snprintf_s`; los argumentos de puntero a `_snwprintf_s` son cadenas de carácter ancho. La detección de errores de codificación en `_snwprintf_s` puede diferir de la de `_snprintf_s`.`_snwprintf_s`, como `swprintf_s`, escribe el resultado en una cadena en lugar de a un destino de tipo `FILE`.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina el requisito de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes. Para obtener más información, consulta [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_sntprintf_s`|`_snprintf_s`|`_snprintf_s`|`_snwprintf_s`|  
|`_sntprintf_s_l`|`_snprintf_s_l`|`_snprintf_s_l`|`_snwprintf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_snprintf_s`, `_snprintf_s_l`|\<stdio.h\>|  
|`_snwprintf_s`, `_snwprintf_s_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_snprintf_s.cpp  
// compile with: /MTd  
  
// These #defines enable secure template overloads  
// (see last part of Examples() below)  
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1   
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT 1  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <string.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
#include <errno.h>  
  
// This example uses a 10-byte destination buffer.  
  
int snprintf_s_tester( const char * fmt, int x, size_t count )  
{  
   char dest[10];  
  
   printf( "\n" );  
  
   if ( count == _TRUNCATE )  
      printf( "%zd-byte buffer; truncation semantics\n",  
               _countof(dest) );  
   else  
      printf( "count = %zd; %zd-byte buffer\n",  
               count, _countof(dest) );  
  
   int ret = _snprintf_s( dest, _countof(dest), count, fmt, x );  
  
   printf( "    new contents of dest: '%s'\n", dest );  
  
   return ret;  
}  
  
void Examples()  
{  
   // formatted output string is 9 characters long: "<<<123>>>"  
   snprintf_s_tester( "<<<%d>>>", 121, 8 );  
   snprintf_s_tester( "<<<%d>>>", 121, 9 );  
   snprintf_s_tester( "<<<%d>>>", 121, 10 );  
  
   printf( "\nDestination buffer too small:\n" );  
  
   snprintf_s_tester( "<<<%d>>>", 1221, 10 );  
  
   printf( "\nTruncation examples:\n" );  
  
   int ret = snprintf_s_tester( "<<<%d>>>", 1221, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
  
   ret = snprintf_s_tester( "<<<%d>>>", 121, _TRUNCATE );  
   printf( "    truncation %s occur\n", ret == -1 ? "did"  
                                                  : "did not" );  
   printf( "\nSecure template overload example:\n" );  
  
   char dest[10];  
   _snprintf( dest, 10, "<<<%d>>>", 12321 );  
   // With secure template overloads enabled (see #defines  
   // at top of file), the preceding line is replaced by  
   //    _snprintf_s( dest, _countof(dest), 10, "<<<%d>>>", 12345 );  
   // Instead of causing a buffer overrun, _snprintf_s invokes  
   // the invalid parameter handler.  
   // If secure template overloads were disabled, _snprintf would  
   // write 10 characters and overrun the dest buffer.  
   printf( "    new contents of dest: '%s'\n", dest );  
}  
  
void myInvalidParameterHandler(  
   const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter handler invoked: %s\n", expression);  
}  
  
int main( void )  
{  
   _invalid_parameter_handler oldHandler, newHandler;  
  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   Examples();  
}  
```  
  
```Output  
  
Count = 8; nuevo contenido de búfer de 10 bytes de destino: ' <<< 121 >> ' count = 9; nuevo contenido de búfer de 10 bytes de destino: '<<< 121 >>> ' count = 10; nuevo contenido de búfer de 10 bytes de destino: '<<< 121 >>> ' búfer de destino demasiado pequeño: count = 10; controlador de parámetro no válido del búfer de 10 bytes invoca: ("Búfer demasiado pequeño", 0) nuevo contenido de destino: '' ejemplos de truncamiento: búfer de 10 bytes; nuevo contenido de semántica de truncamiento de destino: ' <<< 1221 >> ' truncar el búfer de 10 bytes; nuevo contenido de semántica de truncamiento de dest: truncamiento de '<<< 121 >>> ' no ha producido el ejemplo de sobrecarga de plantilla seguras: invoca el controlador de parámetros no válidos: ("Búfer demasiado pequeño", 0) nuevo contenido de destino: ''  
```  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)