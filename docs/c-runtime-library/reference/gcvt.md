---
title: "_gcvt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_gcvt"
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
  - "_gcvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt (función)"
  - "conversiones, de punto flotante a cadenas"
  - "CVTBUFSIZE"
  - "funciones de punto flotante, convertir número a cadena"
  - "gcvt (función)"
  - "números, convertir a cadenas"
  - "cadenas [C++], convertir de punto flotante"
ms.assetid: 5761411e-c06b-409a-912f-810fe7f4bcb5
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _gcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un valor de punto flotante a una cadena, que almacena en un búfer.  Una versión más segura de esta función está disponible; vea [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md).  
  
## Sintaxis  
  
```  
char *_gcvt(   
   double value,  
   int digits,  
   char *buffer   
);  
```  
  
#### Parámetros  
 `value`  
 Valor que se va a convertir.  
  
 `digits`  
 Número de dígitos significativos almacenados.  
  
 `buffer`  
 Ubicación de almacenamiento del resultado.  
  
## Valor devuelto  
 `_gcvt` devuelve un puntero a la cadena de dígitos.  
  
## Comentarios  
 La función de `_gcvt` convierte `value` flotante en una cadena de caracteres \(que incluye un separador decimal y un byte posible de signo\) y almacena la cadena en `buffer`.  `buffer` debe ser suficiente para alojar el valor convertido más un carácter null de terminación, que se agrega automáticamente.  Si un tamaño de búfer de `digits` \+ 1 se utiliza, la función sobrescribe el fin del búfer.  Esto es porque la cadena convertida incluye un separador decimal y puede contener el signo y la información del exponente.  No hay disponible para el desbordamiento.  `_gcvt` intenta generar los dígitos de `digits` en formato decimal.  Si no puede, genera los dígitos de `digits` en formato exponencial.  Los ceros finales se pueden suprimir en la conversión.  
  
 `buffer` de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  
  
 Esta función valida sus parámetros.  Si `buffer` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `NULL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_gcvt`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_gcvt.c  
// compile with: /W3  
#include <stdlib.h>  
#include <stdio.h>  
#include <string.h>  
  
int main( void )  
{  
   char buffer[_CVTBUFSIZE];  
   double value = -1234567890.123;  
   printf( "The following numbers were converted by _gcvt(value,12,buffer):\n" );  
   _gcvt( value, 12, buffer ); // C4996  
   // Note: _gcvt is deprecated; consider using _gcvt_s instead  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value *= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
  
   printf( "\n" );  
   value = -12.34567890123;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
   value /= 10;  
   _gcvt( value, 12, buffer ); // C4996  
   printf( "buffer: '%s' (%d chars)\n", buffer, strlen(buffer) );  
}  
```  
  
  **Los números siguientes se convierten por el \_gcvt \(valor, 12, búfer\):**  
**búfer: “\- 1234567890,12 " \(14 caracteres\)**  
**búfer: “\- 12345678901,2 " \(14 caracteres\)**  
**búfer: “\- 123456789012 " \(13 caracteres\)**  
**búfer: “\- 1.23456789012e\+012” \(19 caracteres\)**  
**búfer: “\- 12,3456789012 " \(14 caracteres\)**  
**búfer: “\- 1,23456789012 " \(14 caracteres\)**  
**búfer: “\- 0,123456789012 " \(15 caracteres\)**  
**búfer: “\- 1.23456789012e\-002” \(19 caracteres\)**   
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)