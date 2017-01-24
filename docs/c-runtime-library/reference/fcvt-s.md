---
title: "_fcvt_s | Microsoft Docs"
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
  - "_fcvt_s"
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
  - "fcvt_s"
  - "_fcvt_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_fcvt_s (función)"
  - "convertir punto flotante, a cadenas"
  - "fcvt_s (función)"
  - "funciones de punto flotante, convertir número a cadena"
ms.assetid: 48671197-1d29-4c2b-a5d8-d2368f5f68a1
caps.latest.revision: 27
caps.handback.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un número en punto flotante en una cadena.  Ésta es una versión de [\_fcvt](../../c-runtime-library/reference/fcvt.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _fcvt_s(   
   char* buffer,  
   size_t sizeInBytes,  
   double value,  
   int count,  
   int *dec,  
   int *sign   
);  
template <size_t size>  
errno_t _fcvt_s(   
   char (&buffer)[size],  
   double value,  
   int count,  
   int *dec,  
   int *sign   
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 El búfer proporcionado que contendrá el resultado de la conversión.  
  
 \[in\] `sizeInBytes`  
 El tamaño del búfer en bytes.  
  
 \[in\] `value`  
 Número que se va a convertir.  
  
 \[in\] `count`  
 Número de dígitos situados a continuación del signo decimal.  
  
 \[out\] `dec`  
 Puntero a la posición de separador decimal almacenada.  
  
 \[out\] `sign`  
 Puntero al marcador almacenado de signo.  
  
## Valor devuelto  
 Cero si correctamente.  El valor devuelto es un código de error si hay un error.  Los códigos de error se definen en Errno.h.  Para obtener una lista de estos errores, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 En el caso de un parámetro no válido, como se muestra en la tabla siguiente, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### Condiciones de error  
  
|`buffer`|`sizeInBytes`|predeterminado|count|diciembre|sign|Devolución|Valor de `buffer`|  
|--------------|-------------------|--------------------|-----------|---------------|----------|----------------|-----------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|No modificado.|  
|No `NULL` \(señala memoria válido\)|\<\=0|any|any|any|any|`EINVAL`|No modificado.|  
|any|any|any|any|`NULL`|any|`EINVAL`|No modificado.|  
|any|any|any|any|any|`NULL`|`EINVAL`|No modificado.|  
  
 **Problemas de seguridad**  
  
 `_fcvt_s` podría generar una infracción de acceso si `buffer` no señala memoria válida y no es `NULL`.  
  
## Comentarios  
 La función de `_fcvt_s` convierte un número en punto flotante a una cadena de caracteres terminada en null.  El parámetro de `value` es el número de punto flotante que se va a convertir.  `_fcvt_s` almacena los dígitos de `value` como cadena y anexa un carácter null \(“\\0”\).  El parámetro de `count` especifica el número de dígitos que se almacenarán después del separador decimal.  Exceso de dígitos se redondean a to los lugares de `count` .  Si hay menos que los dígitos de `count` de precisión, la cadena se rellena con ceros.  
  
 Sólo dígitos se almacenan en la cadena.  La posición del separador decimal y el signo de `value` se pueden obtener de `dec` y de `sign` después de la llamada.  Los puntos del parámetro de `dec` a un valor entero; este valor entero proporciona la posición del separador decimal en cuanto al principio de la cadena.  Un valor entero cero o negativo indica que el separador decimal se encuentra a la izquierda del primer dígito.  Los puntos de `sign` de parámetros a un entero que indica el signo de `value`.  El entero se establece en 0 si `value` es positivo y se establece en un número distinto de cero si `value` es negativo.  
  
 Un búfer de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  
  
 La diferencia entre `_ecvt_s` y `_fcvt_s` está en la del parámetro de `count` .  `_ecvt_s` interpreta `count` como el número total de dígitos en la cadena de salida, y `_fcvt_s` interpreta la c`ount` como el número de dígitos después del separador decimal.  
  
 En C\+\+, mediante esta función es simplificado por una sobrecarga de plantilla; la sobrecarga puede deducir longitud de búfer automáticamente, lo que elimina la necesidad de especificar un argumento size.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 La versión de depuración de esta función primero rellena el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`_fcvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
 **Bibliotecas:** Todas las versiones de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// fcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _fcvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_fcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Valor convertido: 120000**   
## Equivalente en .NET Framework  
 <xref:System.Convert.ToString%2A>  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)