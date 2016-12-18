---
title: "_ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l | Microsoft Docs"
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
  - "_ismbcalpha"
  - "_ismbcalnum"
  - "_ismbcdigit"
  - "_ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_ismbcdigit"
  - "ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha"
  - "ismbcalnum"
  - "ismbcdigit"
  - "ismbcalpha"
  - "_ismbcalnum_l"
  - "_ismbcalnum"
  - "ismbcdigit_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcalnum (función)"
  - "_ismbcalnum_l (función)"
  - "_ismbcalpha (función)"
  - "_ismbcalpha_l (función)"
  - "_ismbcdigit (función)"
  - "_ismbcdigit_l (función)"
  - "ismbcalnum (función)"
  - "ismbcalnum_l (función)"
  - "ismbcalpha (función)"
  - "ismbcalpha_l (función)"
  - "ismbcdigit (función)"
  - "ismbcdigit_l (función)"
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcalnum, _ismbcalnum_l, _ismbcalpha, _ismbcalpha_l, _ismbcdigit, _ismbcdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Comprueba si un carácter multibyte es un carácter alfanumérico, alfa o de dígito.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _ismbcalnum  
(  
   unsigned int c   
);  
int _ismbcalnum_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcalpha  
(  
   unsigned int c   
);  
int _ismbcalpha_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcdigit  
(  
   unsigned int c   
);  
int _ismbcdigit_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple.  Si `c`\<\= 255 y hay una rutina `_ismbb` correspondiente \(por ejemplo, `_ismbcalnum` corresponde a `_ismbbalnum`\), el resultado es el valor devuelto de la rutina `_ismbb` correspondiente.  
  
## Comentarios  
 Cada una de estas rutinas prueba si un carácter multibyte dado cumple una condición determinada.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
|Rutina|Condición de prueba|Ejemplo de la página de códigos 932|  
|------------|-------------------------|-----------------------------------------|  
|`_ismbcalnum,_ismbcalnum_l`|Alfanumérico|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa ASCII. Vea los ejemplos de `_ismbcdigit` y `_ismbcalpha`.|  
|`_ismbcalpha,_ismbcalpha_l`|Alfabético|Devuelve cero si y solo si `c` es una representación de un solo byte de una letra inglesa ASCII: 0x41\=\<`c`\<\=0x5A o 0x61\=\<`c`\<\=0x7A, o una letra de katakana: 0xA6\=\<`c`\<\=0xDF.|  
|`_ismbcdigit,_ismbcdigit`|Dígito|Devuelve cero si y solo si `c` es una representación de un solo byte de un dígito ASCII: 0x30\=\<`c`\<\=0x39.|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbcalnum,_ismbcalnum_l`|\<mbstring.h\>|  
|`_ismbcalpha,_ismbcalpha_l`|\<mbstring.h\>|  
|`_ismbcdigit,_ismbcdigit_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
  
-   [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
-   [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
-   No es aplicable a `_ismbcalnum`. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [\_ismbc \(Rutinas\)](../../c-runtime-library/ismbc-routines.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb \(Rutinas\)](../../c-runtime-library/ismbb-routines.md)