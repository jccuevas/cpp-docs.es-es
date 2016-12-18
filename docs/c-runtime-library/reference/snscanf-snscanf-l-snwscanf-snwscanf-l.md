---
title: "_snscanf, _snscanf_l, _snwscanf, _snwscanf_l | Microsoft Docs"
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
  - "_snwscanf"
  - "_snscanf_l"
  - "_snscanf"
  - "_snwscanf_l"
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
  - "_snscanf"
  - "_snscanf_l"
  - "_snwscanf"
  - "snscanf_l"
  - "snscanf"
  - "_sntscanf_l"
  - "_sntscanf"
  - "_snwscanf_l"
  - "sntscanf_l"
  - "sntscanf"
  - "snwscanf"
  - "snwscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_snscanf (función)"
  - "_snscanf_l (función)"
  - "_sntscanf (función)"
  - "_sntscanf_l (función)"
  - "_snwscanf (función)"
  - "_snwscanf_l (función)"
  - "leer datos, cadenas"
  - "snscanf (función)"
  - "snscanf_l (función)"
  - "sntscanf (función)"
  - "sntscanf_l (función)"
  - "snwscanf (función)"
  - "snwscanf_l (función)"
  - "cadenas [C++], leer"
  - "cadenas [C++], leer datos de"
ms.assetid: da1ac890-f905-4cd7-954b-3c90957b5551
caps.latest.revision: 24
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _snscanf, _snscanf_l, _snwscanf, _snwscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee dio formato datos de una longitud especificada de una cadena.  Hay disponibles versiones más seguras de estas funciones; vea [\_snscanf\_s, \_snscanf\_s\_l, \_snwscanf\_s, \_snwscanf\_s\_l](../../c-runtime-library/reference/snscanf-s-snscanf-s-l-snwscanf-s-snwscanf-s-l.md).  
  
## Sintaxis  
  
```  
int __cdecl _snscanf(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   ...  
);  
```  
  
#### Parámetros  
 `input`  
 Cadena de entrada a examinar.  
  
 `length`  
 Número de caracteres a examinar en `input`.  
  
 `format`  
 Uno o varios especificadores de formato.  
  
 `... (optional)`  
 Las variables que se usarán para almacenar los valores extrajeron de la cadena de entrada de los especificadores de formato en `format`.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Ambas funciones devuelven el número de campos convierten y asignados correctamente; el valor devuelto no incluye los campos que se leyeron pero no asignados.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  Para obtener más información, vea [sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md).  
  
 Si `input` o `format` es un puntero de `NULL` , o si `length` es menor o igual que cero, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Esta función es como `sscanf` salvo que proporciona la capacidad de especificar un número de caracteres fijo para examinar de la cadena de entrada.  Para obtener más información, vea [sscanf](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md).  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_sntscanf`|`_snscanf`|`_snscanf`|`_snwscanf`|  
|`_sntscanf_l`|`_snscanf_l`|`_snscanf_l`|`_snwscanf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_snscanf`, `_snscanf_l`|\<stdio.h\>|  
|`_snwscanf`, `_snwscanf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_snscanf.c  
// compile with: /W3  
  
#include <stdio.h>  
int main( )  
{  
   char  str1[] = "15 12 14...";  
   wchar_t  str2[] = L"15 12 14...";  
   char  s1[3];  
   wchar_t  s2[3];  
   int   i;  
   float fp;  
  
   i = _snscanf( str1, 6,  "%s %f", s1, &fp); // C4996  
   // Note: _snscanf is deprecated; consider using _snscanf_s instead  
   printf("_snscanf converted %d fields: ", i);  
   printf("%s and %f\n", s1, fp);  
  
   i = _snwscanf( str2, 6,  L"%s %f", s2, &fp); // C4996  
   // Note: _snwscanf is deprecated; consider using _snwscanf_s instead  
   wprintf(L"_snwscanf converted %d fields: ", i);  
   wprintf(L"%s and %f\n", s2, fp);  
}  
```  
  
  **el \_snscanf sería 2 campos: 15 y 12,000000**  
**el \_snwscanf sería 2 campos: 15 y 12,000000**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [scanf \(Especificación de ancho\)](../../c-runtime-library/scanf-width-specification.md)