---
title: "isascii, __isascii, iswascii | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswascii"
  - "__isascii"
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
  - "iswascii"
  - "istascii"
  - "__isascii"
  - "_istascii"
  - "isascii"
  - "ctype/isascii"
  - "ctype/__isascii"
  - "corecrt_wctype/iswascii"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__isascii (función)"
  - "_isascii (función)"
  - "isascii (función)"
  - "_istascii (función)"
  - "istascii (función)"
  - "iswascii (función)"
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# isascii, __isascii, iswascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un determinado carácter es un carácter ASCII.  
  
## Sintaxis  
  
```  
int __isascii(   
   int c   
);  
int iswascii(   
   wint_t c   
);  
#define isascii __isascii  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve cero si `c` es una representación concreta de un carácter ASCII.`__isascii` Devuelve un valor distinto de cero si `c` es un carácter ASCII \(en el intervalo de 0 x 00 a 0x7F\).`iswascii` Devuelve un valor distinto de cero si `c` es una representación de caracteres anchos de un carácter ASCII. Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
## Comentarios  
 Ambos `__isascii` y `iswascii` se implementan como macros a menos que se define la macro de preprocesador de \_CTYPE\_DISABLE\_MACROS.  
  
 Por motivos de compatibilidad `isascii` se implementa como un solo si macro [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) no está definido o está definido como 0; de lo contrario, no está definido.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isascii`, `__isascii`|C: \< ctype.h \><br /><br /> C\+\+: \< cctype \> o \< ctype.h \>|  
|`iswascii`|C: \< wctype.h \>, \< ctype.h \> o \< wchar.h \><br /><br /> C\+\+: \< cwctype \>, \< cctype \>, \< wctype.h \>, \< ctype.h \> o \< wchar.h \>|  
  
 El `isascii`, `__isascii` y `iswascii` funciones son específicos de Microsoft. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)