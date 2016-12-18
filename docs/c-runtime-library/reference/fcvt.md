---
title: "_fcvt | Microsoft Docs"
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
  - "_fcvt"
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
  - "_fcvt"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fcvt (función)"
  - "convertir punto flotante, a cadenas"
  - "fcvt (función)"
  - "funciones de punto flotante"
  - "funciones de punto flotante, convertir número a cadena"
ms.assetid: 74584c88-f0dd-4907-8fca-52da5df583f5
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fcvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un número en punto flotante en una cadena.  Una versión más segura de esta función está disponible; vea [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md).  
  
## Sintaxis  
  
```  
char *_fcvt(   
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
```  
  
#### Parámetros  
 `value`  
 Número que se va a convertir.  
  
 `count`  
 Número de dígitos situados a continuación del signo decimal.  
  
 `dec`  
 Puntero a la posición de separador decimal almacenada.  
  
 `sign`  
 Puntero al marcador almacenado de signo.  
  
## Valor devuelto  
 `_fcvt` devuelve un puntero a la cadena de dígitos, NULL en error.  
  
## Comentarios  
 La función de `_fcvt` convierte un número en punto flotante a una cadena de caracteres terminada en null.  El parámetro de `value` es el número de punto flotante que se va a convertir.  `_fcvt` almacena los dígitos de `value` como cadena y anexa un carácter null \(“\\0”\).  El parámetro de `count` especifica el número de dígitos que se almacenarán después del separador decimal.  Exceso de dígitos se redondean a to los lugares de `count` .  Si hay menos que los dígitos de `count` de precisión, la cadena se rellena con ceros.  
  
 El número total de dígitos devueltos por `_fcvt` no superará `_CVTBUFSIZE`.  
  
 Sólo dígitos se almacenan en la cadena.  La posición del separador decimal y el signo de `value` se pueden obtener de `dec` y de signo después de la llamada.  Los puntos del parámetro de `dec` a un valor entero; este valor entero proporciona la posición del separador decimal en cuanto al principio de la cadena.  Un valor entero cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito.  Los puntos de `sign` de parámetros a un entero que indica el signo de `value`.  El entero se establece en 0 si `value` es positivo y se establece en un número distinto de cero si `value` es negativo.  
  
 La diferencia entre `_ecvt` y `_fcvt` está en la del parámetro de `count` .  `_ecvt` interpreta `count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt` interpreta `count` como el número de dígitos después del separador decimal.  
  
 `_ecvt` y `_fcvt` utilizan un único búfer estáticamente asignado para la conversión.  Cada llamada a una de estas rutinas destruye los resultados de la llamada anterior.  
  
 Esta función valida sus parámetros.  Si `dec` o `sign` es NULL, o `count` es 0, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve NULL.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fcvt`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fcvt.c  
// compile with: /W3  
// This program converts the constant  
// 3.1415926535 to a string and sets the pointer  
// buffer to point to that string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int  decimal, sign;  
   char *buffer;  
   double source = 3.1415926535;  
  
   buffer = _fcvt( source, 7, &decimal, &sign ); // C4996  
   // Note: _fcvt is deprecated; consider using _fcvt_s instead  
   printf( "source: %2.10f   buffer: '%s'   decimal: %d   sign: %d\n",  
            source, buffer, decimal, sign );  
}  
```  
  
  **origen: búfer 3,1415926535: “31415927 " decimal: 1 firmados: 0**   
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)