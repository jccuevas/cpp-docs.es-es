---
title: "_vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l | Microsoft Docs"
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
  - "_vscprintf"
  - "_vscprintf_l"
  - "_vscwprintf_l"
  - "_vscwprintf"
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
  - "vscprintf_l"
  - "vscwpeintf"
  - "_vscwprintf"
  - "_vsctprintf"
  - "_vscprintf"
  - "vscwprintf_l"
  - "vscprintf"
  - "_vscwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vscprintf (función)"
  - "_vscprintf_l (función)"
  - "_vsctprintf (función)"
  - "_vsctprintf_l (función)"
  - "_vscwprintf (función)"
  - "_vscwprintf_l (función)"
  - "texto con formato [C++]"
  - "vscprintf (función)"
  - "vscprintf_l (función)"
  - "vsctprintf (función)"
  - "vsctprintf_l (función)"
  - "vscwprintf (función)"
  - "vscwprintf_l (función)"
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vscprintf, _vscprintf_l, _vscwprintf, _vscwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el número de caracteres de la cadena con formato mediante un puntero a una lista de argumentos.  
  
## Sintaxis  
  
```  
int _vscprintf(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `argptr`  
 Puntero a la lista de argumentos.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Valor devuelto  
 `_vscprintf` devuelve el número de caracteres que se generará si la cadena indicada por a la lista de argumentos se imprimirá o enviada a un archivo o un búfer mediante los códigos de formato especificados.  El valor devuelto no incluye el carácter null de terminación.  `_vscwprintf` realiza la misma función por caracteres anchos.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
 Si `format` es un puntero nulo, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
## Comentarios  
 Cada `argument` \(si existe\) se convierte según la especificación correspondiente de formato en `format`.  El formato consta de caracteres ordinarios y tiene el mismo formato y función que el argumento `format` para [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
> [!IMPORTANT]
>  Asegúrese de que si `format` es una cadena definida por el usuario, sea null finalizada y tiene el número y el tipo correctos de parámetros.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vsctprintf`|`_vscprintf`|`_vscprintf`|`_vscwprintf`|  
|`_vsctprintf_l`|`_vscprintf_l`|`_vscprintf_l`|`_vscwprintf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_vscprintf`, `_vscprintf_l`|\<stdio.h\>|  
|`_vscwprintf`, `_vscwprintf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo para [vsprintf](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)