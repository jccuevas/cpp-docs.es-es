---
title: "iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iscntrl"
  - "_iswcntrl_l"
  - "_iscntrl_l"
  - "iswcntrl"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_istcntrl_l"
  - "_iswcntrl_l"
  - "iswcntrl"
  - "_iscntrl_l"
  - "iscntrl"
  - "_istcntrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_iscntrl_l (función)"
  - "_istcntrl (función)"
  - "_istcntrl_l (función)"
  - "_iswcntrl_l (función)"
  - "iscntrl (función)"
  - "istcntrl (función)"
  - "iswcntrl (función)"
ms.assetid: 616eebf9-aed4-49ba-ba2c-8677c8fe6fb5
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter de control.  
  
## Sintaxis  
  
```  
int iscntrl(   
   int c   
);  
int iswcntrl(   
   wint_t c   
);  
int _iscntrl_l(   
   int c,  
   _locale_t locale  
);  
int _iswcntrl_l(   
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter de control.  `iscntrl` devuelve un valor distinto de cero si `c` es un carácter de control \(0x00 – 0x1F o 0x7F\).  `iswcntrl` devuelve un valor distinto de cero si `c` es un carácter ancho de control.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `iscntrl` e `_iscntrl_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istcntrl`|`iscntrl`|`iscntrl`|`iswcntrl`|  
|`_istcntrl_l`|`_iscntrl_l`|`_iscntrl_l`|`_iswcntrl_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`iscntrl`|\<ctype.h\>|  
|`iswcntrl`|\<ctype.h\> o \<wchar.h\>|  
|`_iscntrl_l`|\<ctype.h\>|  
|`_iswcntrl_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsControl](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)