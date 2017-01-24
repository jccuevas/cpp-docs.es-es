---
title: "_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l | Microsoft Docs"
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
  - "_atoldbl"
  - "_atoldbl_l"
  - "_atodbl"
  - "_atoflt"
  - "_atoflt_l"
  - "_atodbl_l"
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
  - "_atoflt"
  - "_atoflt_l"
  - "atodbl_l"
  - "atoflt_l"
  - "_atoldbl"
  - "_atoldbl_l"
  - "atodbl"
  - "_atodbl_l"
  - "atoldbl"
  - "atoflt"
  - "atoldbl_l"
  - "_atodbl"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_atodbl (función)"
  - "_atoldbl_l (función)"
  - "atoflt (función)"
  - "atoflt_l (función)"
  - "atoldbl (función)"
  - "_atoldbl (función)"
  - "atodbl_l (función)"
  - "_atoflt_l (función)"
  - "atoldbl_l (función)"
  - "atodbl (función)"
  - "conversión de cadenas, a valores de punto flotante"
  - "_atoflt (función)"
  - "_atodbl_l (función)"
ms.assetid: 2d2530f4-4bd4-42e3-8083-f2d2fbc8432a
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en double \(`_atodbl`\), long double \(`_atoldbl`\) o float \(`_atoflt`\).  
  
## Sintaxis  
  
```  
int _atodbl(  
   _CRT_DOUBLE * value,  
   char * str  
);  
int _atodbl_l (  
   _CRT_DOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoldbl(  
   _LDOUBLE * value,  
   char * str  
);  
int _atoldbl_l (  
   _LDOUBLE * value,  
   char * str,  
   locale_t locale  
);  
int _atoflt(  
   _CRT_FLOAT * value,  
   const char * str  
);  
int _atoflt_l(  
   _CRT_FLOAT * value,  
   const char * str,  
   locale_t locale  
);  
```  
  
#### Parámetros  
 `value`  
 Valor double, long double o float que se genera al convertir la cadena en un valor de punto flotante.  Estos valores se agrupan en una estructura.  
  
 `str`  
 Cadena que se va a analizar para convertirla en un valor de punto flotante.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, devuelve 0.  Los códigos de error posibles son `_UNDERFLOW` o `_OVERFLOW`, que se definen en el archivo de encabezado Math.h.  
  
## Comentarios  
 Estas funciones convierten una cadena en un valor de punto flotante.  La diferencia entre estas funciones y la familia de funciones `atof` es que estas funciones no generan código de punto flotante y no producen excepciones de hardware.  En lugar de ello, las condiciones de error se notifican como códigos de error.  
  
 Si una cadena no tiene una interpretación válida como valor de punto flotante, `value` se establece en cero y el valor devuelto es cero.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` son idénticas a las versiones que no lo tienen, salvo que utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual.  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`_atodbl`, `_atoldbl`, `_atoflt`<br /><br /> `_atodbl_l`, `_atoldbl_l`, `_atoflt_l`|\<stdlib.h\>|  
  
## Ejemplo  
  
```  
// crt_atodbl.c  
// Uses _atodbl to convert a string to a double precision  
// floating point value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main()  
{  
   char str1[256] = "3.141592654";  
   char abc[256] = "abc";  
   char oflow[256] = "1.0E+5000";  
   _CRT_DOUBLE dblval;  
   _CRT_FLOAT fltval;  
   int retval;  
  
   retval = _atodbl(&dblval, str1);  
  
   printf("Double value: %lf\n", dblval.x);  
   printf("Return value: %d\n\n", retval);  
  
   retval = _atoflt(&fltval, str1);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // A non-floating point value: returns 0.  
   retval = _atoflt(&fltval, abc);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   // Overflow.  
   retval = _atoflt(&fltval, oflow);  
   printf("Float value: %f\n", fltval.f);  
   printf("Return value: %d\n\n", retval);  
  
   return 0;  
}  
```  
  
  **Valor double: 3,141593**  
**Valor devuelto: 0**  
**Valor float: 3,141593**  
**Valor devuelto: 0**  
**Valor float: 0,000000**  
**Valor devuelto: 0**  
**Valor float: 1.\#INF00**  
**Valor devuelto: 3**   
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)