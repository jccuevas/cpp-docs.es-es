---
title: "_scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l | Microsoft Docs"
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
  - "_scwprintf_p"
  - "_scprintf_p_l"
  - "_scwprintf_p_l"
  - "_scprintf_p"
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
  - "_scwprintf_p_l"
  - "_sctprintf_p"
  - "scprintf_p_l"
  - "scprintf_p"
  - "_sctprintf_p_l"
  - "scwprintf_p"
  - "_scprintf_p_l"
  - "scwprintf_p_l"
  - "_scprintf_p"
  - "_scwprintf_p"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_scprintf_p (función)"
  - "_scprintf_p_l (función)"
  - "_sctprintf_p (función)"
  - "_sctprintf_p_l (función)"
  - "_scwprintf_p (función)"
  - "_scwprintf_p_l (función)"
  - "scprintf_p (función)"
  - "scprintf_p_l (función)"
  - "sctprintf_p (función)"
  - "sctprintf_p_l (función)"
  - "scwprintf_p (función)"
  - "scwprintf_p_l (función)"
ms.assetid: 8390d1e1-2826-47a4-851f-6635a88087cc
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _scprintf_p, _scprintf_p_l, _scwprintf_p, _scwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el número de caracteres de la cadena con formato, con la capacidad de especificar el orden en el que los parámetros se utilizan en la cadena de formato.  
  
## Sintaxis  
  
```  
int _scprintf_p(  
   const char *format [,  
   argument] ...   
);  
int _scprintf_p_l(  
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _scwprintf_p (  
   const wchar_t *format [,  
   argument] ...   
);  
int _scwprintf_p _l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
);  
```  
  
#### Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve el número de caracteres que se generará si se imprimiera o se enviara la cadena a un archivo o un búfer mediante los códigos de formato especificados.  El valor devuelto no incluye el carácter null de terminación.  `_scwprintf_p` realiza la misma función por caracteres anchos.  
  
 La diferencia entre `_scprintf_p` y `_scprintf` es que `_scprintf_p` admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato.  Para obtener más información, vea [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 Si `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada `argument` \(si existe\) se convierte según la especificación correspondiente de formato en `format`.  El formato consta de caracteres ordinarios y tiene el mismo formato y función que el argumento `format` para [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md).  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_sctprintf_p`|`_scprintf_p`|`_scprintf_p`|`_scwprintf_p`|  
|`_sctprintf_p_l`|`_scprintf_p_l`|`_scprintf_p_l`|`_scwprintf_p_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_scprintf_p`, `_scprintf_p_l`|\<stdio.h\>|  
|`_scwprintf_p`, `_scwprintf_p_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_scprintf, \_scprintf\_l, \_scwprintf, \_scwprintf\_l](../../c-runtime-library/reference/scprintf-scprintf-l-scwprintf-scwprintf-l.md)   
 [\_printf\_p, \_printf\_p\_l, \_wprintf\_p, \_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)