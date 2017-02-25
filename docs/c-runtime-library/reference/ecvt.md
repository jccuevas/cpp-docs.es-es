---
title: "ecvt | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ecvt"
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
  - "ecvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ecvt (función)"
ms.assetid: a916eb05-92d1-4b5c-8563-093acdb49dc8
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# _ecvt
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un número de `double` en una cadena.  Una versión más segura de esta función está disponible; vea [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md).  
  
## Sintaxis  
  
```  
char *_ecvt(   
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
 Número de dígitos almacenados.  
  
 `dec`  
 Posición de separador decimal almacenada.  
  
 `sign`  
 Signo de número convertido.  
  
## Valor devuelto  
 `_ecvt` devuelve un puntero a la cadena de dígitos; NULL si se ha producido un error.  
  
## Comentarios  
 La función de `_ecvt` convierte un número en punto flotante a una cadena de caracteres.  El parámetro de `value` es el número de punto flotante que se va a convertir.  Esta función almacena hasta `count` dígitos de `value` como cadena y anexa un carácter null \(“\\0”\).  Si el número de dígitos en `value` supera `count`, se redondea el dígito de orden inferior.  Si hay menos que los dígitos de `count` , la cadena se rellena con ceros.  
  
 El número total de dígitos devueltos por `_ecvt` no superará `_CVTBUFSIZE`.  
  
 Sólo dígitos se almacenan en la cadena.  La posición del separador decimal y el signo de `value` se pueden obtener de `dec` y de `sign` después de la llamada.  Los puntos del parámetro de `dec` a un valor entero que indica la posición del separador decimal con respecto al principio de la cadena.  Un 0 o un valor entero negativo indica que el separador decimal se encuentra a la izquierda del primer dígito.  Los puntos del parámetro de `sign` a un entero que indica el signo de número convertido.  Si el valor entero es 0, el número es positivo.  Si no, el número es negativo.  
  
 La diferencia entre `_ecvt` y `_fcvt` está en la del parámetro de `count` .  `_ecvt` interpreta `count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt` interpreta `count` como el número de dígitos después del separador decimal.  
  
 `_ecvt` y `_fcvt` utilizan un único búfer estáticamente asignado para la conversión.  Cada llamada a una de estas rutinas destruye el resultado de la llamada anterior.  
  
 Esta función valida sus parámetros.  Si `dec` o `sign` es NULL, o `count` es 0, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y se devuelve NULL.  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_ecvt`|\<stdlib.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_ecvt.c  
// compile with: /W3  
// This program uses _ecvt to convert a  
// floating-point number to a character string.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int     decimal,   sign;  
   char    *buffer;  
   int     precision = 10;  
   double  source = 3.1415926535;  
  
   buffer = _ecvt( source, precision, &decimal, &sign ); // C4996  
   // Note: _ecvt is deprecated; consider using _ecvt_s instead  
   printf( "source: %2.10f   buffer: '%s'  decimal: %d  sign: %d\n",  
           source, buffer, decimal, sign );  
}  
```  
  
  **origen: búfer 3,1415926535: “3141592654 " decimal: 1 firmados: 0**   
## Equivalente en .NET Framework  
 [System::Convert::ToString](https://msdn.microsoft.com/en-us/library/system.convert.tostring.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)