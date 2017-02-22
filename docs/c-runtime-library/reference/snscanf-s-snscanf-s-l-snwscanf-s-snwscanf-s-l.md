---
title: "_snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_snwscanf_s_l"
  - "_snwscanf_s"
  - "_snscanf_s"
  - "_snscanf_s_l"
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
  - "_sntscanf_s"
  - "snscanf_s"
  - "_snwscanf_s_l"
  - "sntscanf_s_l"
  - "snwscanf_s_l"
  - "snwscanf_s"
  - "_snscanf_s"
  - "_snwscanf_s"
  - "snscanf_s_l"
  - "_sntscanf_s_l"
  - "_snscanf_s_l"
  - "sntscanf_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_snscanf_s (función)"
  - "_snscanf_s_l (función)"
  - "_sntscanf_s (función)"
  - "_sntscanf_s_l (función)"
  - "_snwscanf_s (función)"
  - "_snwscanf_s_l (función)"
  - "leer datos, cadenas"
  - "snscanf_s (función)"
  - "snscanf_s_l (función)"
  - "sntscanf_s (función)"
  - "sntscanf_s_l (función)"
  - "snwscanf_s (función)"
  - "snwscanf_s_l (función)"
  - "cadenas [C++], leer"
  - "cadenas [C++], leer datos de"
ms.assetid: 72356653-7362-461a-af73-597b9c0a8094
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _snscanf_s, _snscanf_s_l, _snwscanf_s, _snwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee dio formato datos de una longitud especificada de una cadena.  Estas versiones de [\_snscanf, \_snscanf\_l, \_snwscanf, \_snwscanf\_l](../../c-runtime-library/reference/snscanf-snscanf-l-snwscanf-snwscanf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int __cdecl _snscanf_s(  
   const char * input,  
   size_t length,  
   const char * format,  
   ...  
);  
int __cdecl _snscanf_s_l(  
   const char * input,  
   size_t length,  
   const char * format,  
   locale_t locale,  
   ...  
);  
int __cdecl _snwscanf_s(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   ...  
);  
int __cdecl _snwscanf_s_l(  
   const wchar_t * input,  
   size_t length,  
   const wchar_t * format,  
   locale_t locale,  
   …  
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
 Ambas funciones devuelven el número de campos convierten y asignados correctamente; el valor devuelto no incluye los campos que se leyeron pero no asignados.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  Para obtener más información, vea [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).  
  
 Si `input` o `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Esta función es como `sscanf_s` salvo que proporciona la capacidad de especificar un número de caracteres fijo para examinar de la cadena de entrada.  Para obtener más información, vea [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).  
  
 El parámetro de tamaño de búfer se requiere con escribir caracteres de campo `c`, `C`, `s`, `S`, y `[`.  Para obtener más información, vea [scanf \(Caracteres de campo de tipo\)](../../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  El parámetro de tamaño es del tipo `unsigned`, no `size_t`.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_sntscanf_s`|`_snscanf_s`|`_snscanf_s`|`_snwscanf_s`|  
|`_sntscanf_s_l`|`_snscanf_s_l`|`_snscanf_s_l`|`_snwscanf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_snscanf_s`, \_`snscanf_s_l`|\<stdio.h\>|  
|`_snwscanf_s`, `_snwscanf_s_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_snscanf_s.c  
// This example scans a string of   
// numbers, using both the character  
// and wide character secure versions  
// of the snscanf function.  
  
#include <stdio.h>  
  
int main( )  
{  
    char        str1[] = "15 12 14...";  
    wchar_t     str2[] = L"15 12 14...";  
    char        s1[3];  
    wchar_t     s2[3];  
    int         i;  
    float       fp;  
  
    i = _snscanf_s( str1, 6,  "%s %f", s1, 3, &fp);  
    printf_s("_snscanf_s converted %d fields: ", i);  
    printf_s("%s and %f\n", s1, fp);  
  
    i = _snwscanf_s( str2, 6,  L"%s %f", s2, 3, &fp);  
    wprintf_s(L"_snwscanf_s converted %d fields: ", i);  
    wprintf_s(L"%s and %f\n", s2, fp);  
}  
```  
  
  **los \_snscanf\_s convirtieron 2 campos: 15 y 12,000000**  
**los \_snwscanf\_s convirtieron 2 campos: 15 y 12,000000**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [scanf \(Especificación de ancho\)](../../c-runtime-library/scanf-width-specification.md)