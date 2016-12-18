---
title: "ToAscii, __toascii | Microsoft Docs"
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
  - "__toascii"
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
  - "__toascii"
  - "toascii"
  - "ctype/toascii"
  - "ctype/__toascii"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "toascii (función)"
  - "conversión de cadenas, en caracteres ASCII"
  - "__toascii (función)"
  - "Caracteres ASCII, convertir a"
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ToAscii, __toascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte caracteres ASCII de 7 bits por truncamiento.  
  
## Sintaxis  
  
```  
int __toascii(  
   int c   
);  
#define toascii __toascii  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a convertir.  
  
## Valor devuelto  
 `__toascii` Convierte el valor de `c` a ASCII de 7 bits de intervalo y devuelve el resultado. No hay ningún valor devuelto reservado para indicar un error.  
  
## Comentarios  
 El `__toascii` rutina convierte el carácter especificado en un carácter ASCII truncando a los bits de orden inferior 7. No se aplica a ninguna otra transformación.  
  
 El `__toascii` rutina se define como una macro definida la macro de preprocesador de \_CTYPE\_DISABLE\_MACROS. Por motivos de compatibilidad `toascii` se define como una macro solamente cuando [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) no está definido o está definido como 0; de lo contrario, no está definido.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`toascii`, `__toascii`|C: \< ctype.h \><br /><br /> C\+\+: \< cctype \> o \< ctype.h \>|  
  
 El `toascii` macro es una extensión de POSIX, y `__toascii` es una implementación específica de Microsoft de la extensión POSIX. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [to \(Funciones\)](../../c-runtime-library/to-functions.md)