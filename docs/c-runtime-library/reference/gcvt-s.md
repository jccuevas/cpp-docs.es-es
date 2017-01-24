---
title: "_gcvt_s | Microsoft Docs"
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
  - "_gcvt_s"
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
  - "_gcvt_s"
  - "gcvt_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CVTBUFSIZE"
  - "_gcvt_s (función)"
  - "conversiones, de punto flotante a cadenas"
  - "CVTBUFSIZE"
  - "funciones de punto flotante, convertir número a cadena"
  - "gcvt_s (función)"
  - "números, convertir a cadenas"
  - "cadenas [C++], convertir de punto flotante"
ms.assetid: 0a8d8a26-5940-4ae3-835e-0aa6ec1b0744
caps.latest.revision: 30
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _gcvt_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un valor de punto flotante a una cadena.  Ésta es una versión de [\_gcvt](../../c-runtime-library/reference/gcvt.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _gcvt_s(   
   char *buffer,  
   size_t sizeInBytes,  
   double value,  
   int digits   
);  
template <size_t cchStr>  
errno_t _gcvt_s(   
   char (&buffer)[cchStr],  
   double value,  
   int digits   
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 Búfer para almacenar el resultado de la conversión.  
  
 \[in\] `sizeInBytes`  
 Tamaño del búfer.  
  
 \[in\] `value`  
 Valor que se va a convertir.  
  
 \[in\] `digits`  
 Número de dígitos significativos almacenados.  
  
## Valor devuelto  
 Cero si correctamente.  Si un error se produce debido a un parámetro no válido \(vea la tabla siguiente por valores no válidos\), se invoca el controlador no válido del parámetro tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, se devuelve un código de error.  Los códigos de error se definen en Errno.h.  Para obtener una lista de estos errores, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### Condiciones de error  
  
|`buffer`|`sizeInBytes`|`value`|`digits`|Devolución|Valor de `buffer`|  
|--------------|-------------------|-------------|--------------|----------------|-----------------------|  
|`NULL`|any|any|any|`EINVAL`|No modificado.|  
|No `NULL` \(señala memoria válido\)|cero|any|any|`EINVAL`|No modificado.|  
|No `NULL` \(señala memoria válido\)|any|any|\>\= `sizeInBytes`|`EINVAL`|No modificado.|  
  
 **Problemas de seguridad**  
  
 `_gcvt_s` puede generar una infracción de acceso si `buffer` no señala memoria válida y no es `NULL`.  
  
## Comentarios  
 La función de `_gcvt_s` convierte `value` flotante en una cadena de caracteres \(que incluye un separador decimal y un byte posible de signo\) y almacena la cadena en `buffer`.  `buffer` debe ser suficiente para alojar el valor convertido más un carácter null de terminación, que se agrega automáticamente.  Un búfer de longitud `_CVTBUFSIZE` es suficiente para cualquier valor de punto flotante.  Si un tamaño de búfer de `digits` \+ 1 se utiliza, la función no sobrescribirá el fin del búfer, de modo que esté seguro de proporcionar un búfer suficiente para esta operación.  `_gcvt_s` intenta generar los dígitos de `digits` en formato decimal.  Si no puede, genera los dígitos de `digits` en formato exponencial.  Los ceros finales se pueden suprimir en la conversión.  
  
 En C\+\+, mediante esta función es simplificado por una sobrecarga de plantilla; la sobrecarga puede deducir longitud de búfer automáticamente, lo que elimina la necesidad de especificar un argumento size.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
 La versión de depuración de esta función primero rellena el búfer con 0xFD.  Para deshabilitar este comportamiento, use [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|------------|--------------------------|-------------------------|  
|`_gcvt_s`|\<stdlib.h\>|\<error.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Ejemplo  
  
```  
// crt_gcvt_s.c  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main()  
{  
  char buf[_CVTBUFSIZE];  
  int decimal;  
  int sign;  
  int err;  
  
  err = _gcvt_s(buf, _CVTBUFSIZE, 1.2, 5);  
  
  if (err != 0)  
  {  
     printf("_gcvt_s failed with error code %d\n", err);  
     exit(1);  
  }  
  
  printf("Converted value: %s\n", buf);    
  
}  
```  
  
  **Valor convertido: 1,2**   
## Equivalente en .NET Framework  
 <xref:System.Convert.ToString%2A>  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [\_ecvt\_s](../../c-runtime-library/reference/ecvt-s.md)   
 [\_fcvt\_s](../../c-runtime-library/reference/fcvt-s.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)