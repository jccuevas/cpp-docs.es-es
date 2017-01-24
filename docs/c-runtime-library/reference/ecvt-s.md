---
title: "_ecvt_s | Microsoft Docs"
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
  - "_ecvt_s"
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
  - "ecvt_s"
  - "_ecvt_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ecvt_s (función)"
  - "convertir números double"
  - "ecvt_s (función)"
  - "números, convertir"
ms.assetid: d52fb0a6-cb91-423f-80b3-952a8955d914
caps.latest.revision: 25
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ecvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un número de `double` en una cadena.  Ésta es una versión de [\_ecvt](../../c-runtime-library/reference/ecvt.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _ecvt_s(   
   char * _Buffer,  
   size_t _SizeInBytes,  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
);  
template <size_t size>  
errno_t _ecvt_s(   
   char (&_Buffer)[size],  
   double _Value,  
   int _Count,  
   int *_Dec,  
   int *_Sign  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `_Buffer`  
 Relleno con el puntero a la cadena de dígitos, el resultado de la conversión.  
  
 \[in\] `_SizeInBytes`  
 Tamaño del búfer en bytes.  
  
 \[in\] `_Value`  
 Número que se va a convertir.  
  
 \[in\] `_Count`  
 Número de dígitos almacenados.  
  
 \[out\] `_Dec`  
 Posición de separador decimal almacenada.  
  
 \[out\] `_Sign`  
 Signo de número convertido.  
  
## Valor devuelto  
 Cero si correctamente.  El valor devuelto es un código de error si hay un error.  Los códigos de error se definen en Errno.h.  Para obtener más información, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
 En el caso de un parámetro no válido, como se muestra en la tabla siguiente, esta función invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función establece `errno` en `EINVAL` y devuelve `EINVAL`.  
  
### Condiciones de error  
  
|`_Buffer`|`_SizeInBytes`|\_Value|\_Count|\_Dec|\_Sign|Valor devuelto|Valor de `buffer`|  
|---------------|--------------------|-------------|-------------|-----------|------------|--------------------|-----------------------|  
|`NULL`|any|any|any|any|any|`EINVAL`|No modificado.|  
|No `NULL` \(señala memoria válido\)|\<\=0|any|any|any|any|`EINVAL`|No modificado.|  
|any|any|any|any|`NULL`|any|`EINVAL`|No modificado.|  
|any|any|any|any|any|`NULL`|`EINVAL`|No modificado.|  
  
 **Problemas de seguridad**  
  
 `_ecvt_s` podría generar una infracción de acceso si `buffer` no señala memoria válida y no es `NULL`.  
  
## Comentarios  
 La función de `_ecvt_s` convierte un número en punto flotante a una cadena de caracteres.  El parámetro de `_Value` es el número de punto flotante que se va a convertir.  Esta función almacena hasta `count` dígitos de `_Value` como cadena y anexa un carácter null \(“\\0”\).  Si el número de dígitos en `_Value` supera `_Count`, se redondea el dígito de orden inferior.  Si hay menos que los dígitos de `count` , la cadena se rellena con ceros.  
  
 Sólo dígitos se almacenan en la cadena.  La posición del separador decimal y el signo de `_Value` se pueden obtener de `_Dec` y de `_Sign` después de la llamada.  Los puntos del parámetro de `_Dec` a un valor entero que indica la posición del separador decimal con respecto al principio de la cadena.  Un 0 o un valor entero negativo indica que el separador decimal se encuentra a la izquierda del primer dígito.  Los puntos del parámetro de `_Sign` a un entero que indica el signo de número convertido.  Si el valor entero es 0, el número es positivo.  Si no, el número es negativo.  
  
 Un búfer de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  
  
 La diferencia entre `_ecvt_s` y `_fcvt_s` está en la del parámetro de `_Count` .  `_ecvt_s` interpreta `_Count` como el número total de dígitos en la cadena de salida, mientras que `_fcvt_s` interpreta `_Count` como el número de dígitos después del separador decimal.  
  
 En C\+\+, mediante esta función es simplificado por una sobrecarga de plantilla; la sobrecarga puede deducir longitud de búfer automáticamente, lo que elimina la necesidad de especificar un argumento size.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 La versión de depuración de esta función primero rellena el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|Encabezado opcional|  
|-------------|--------------------------|-------------------------|  
|`_ecvt_s`|\<stdlib.h\>|\<errno.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Ejemplo  
  
```  
// ecvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( )  
{  
  char * buf = 0;  
  int decimal;  
  int sign;  
  int err;  
  
  buf = (char*) malloc(_CVTBUFSIZE);  
  err = _ecvt_s(buf, _CVTBUFSIZE, 1.2, 5, &decimal, &sign);  
  
  if (err != 0)  
  {  
     printf("_ecvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Valor convertido: 12000**   
## Equivalente en .NET Framework  
 <xref:System.Convert.ToString%2A>  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt\_s](../../c-runtime-library/reference/gcvt-s.md)