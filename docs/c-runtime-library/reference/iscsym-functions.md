---
title: "iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l | Microsoft Docs"
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
  - "_iswcsym_l"
  - "__iswcsym"
  - "__iscsym"
  - "_iswcsymf_l"
  - "_iscsym_l"
  - "__iswcsymf"
  - "__iscsymf"
  - "_iscsymf_l"
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
  - "_iswcsym_l"
  - "_iswcsymf_l"
  - "iscsymf"
  - "iswcsymf"
  - "__iswcsym"
  - "__iswcsymf"
  - "iscsym"
  - "iswcsym"
  - "__iscsym"
  - "_iscsym_l"
  - "_iscsymf_l"
  - "__iscsymf"
  - "ctype/iscsym"
  - "ctype/iscsymf"
  - "ctype/__iscsym"
  - "ctype/__iscsymf"
  - "ctype/__iscsym_l"
  - "ctype/__iscsymf_l"
  - "ctype/__iswcsym"
  - "ctype/__iswcsymf"
  - "ctype/__iswcsym_l"
  - "ctype/__iswcsymf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "iscsymf_l (función)"
  - "iswsym_l (función)"
  - "_iswcsym_l (función)"
  - "iscsym_l (función)"
  - "_iscsymf_l (función)"
  - "_iswcsymf_l (función)"
  - "_iscsym_l (función)"
  - "__iscsym (función)"
  - "__iswcsymf (función)"
  - "iswsymf_l (función)"
  - "__iscsymf (función)"
  - "__iswcsym (función)"
  - "iscsym (función)"
  - "iscsymf (función)"
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iscsym, iscsymf, __iscsym, __iswcsym, __iscsymf, __iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l, _iswcsymf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determinar si un entero representa un carácter que se puede usar en un identificador.  
  
## Sintaxis  
  
```  
int __iscsym(   
   int c   
);  
int __iswcsym(   
   wint_t c   
);  
int __iscsymf(   
   int c   
);  
int __iswcsymf(   
   wint_t c   
);  
int _iscsym_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsym_l(   
   wint_t c,  
   _locale_t locale  
);  
int _iscsymf_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsymf_l(   
   wint_t c,  
   _locale_t locale  
);  
#define iscsym __iscsym  
#define iscsymf __iscsymf  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.`c` debe estar en el intervalo de 0 a 255 para la versión de caracteres estrechos de la función.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Ambos `__iscsym` y `__iswcsym` devuelven un valor distinto de cero si `c` es una letra, carácter de subrayado o dígito. Ambos `__iscsymf` y `__iswcsymf` devuelven un valor distinto de cero si `c` es una letra o un carácter de subrayado. Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba. Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional. Para obtener más información, consulta [Configuración regional](../../c-runtime-library/locale.md).  
  
## Comentarios  
 Estas rutinas se definen como macros a menos que se define la macro de preprocesador de \_CTYPE\_DISABLE\_MACROS. Cuando se usan las versiones de macro de estas rutinas, los argumentos se pueden evaluar varias veces. Tenga cuidado al utilizar expresiones con efectos secundarios dentro de la lista de argumentos.  
  
 Por compatibilidad con versiones anteriores, `iscsym` y `iscsymf` se definen como macros sólo cuando [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) no está definido o está definido como 0; de lo contrario, no están definidos.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, `_iswcsymf_l`|C: \< ctype.h \><br /><br /> C\+\+: \< cctype \> o \< ctype.h \>|  
  
 El `iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, y `_iswcsymf_l` rutinas son específicos de Microsoft. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)