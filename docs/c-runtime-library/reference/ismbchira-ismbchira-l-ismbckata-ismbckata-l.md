---
title: "_ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l | Microsoft Docs"
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
  - "_ismbckata"
  - "_ismbchira_l"
  - "_ismbchira"
  - "_ismbckata_l"
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
  - "ismbckata_l"
  - "_ismbckata_l"
  - "ismbckata"
  - "ismbchira"
  - "_ismbckata"
  - "ismbchira_l"
  - "_ismbchira_l"
  - "_ismbchira"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbchira (función)"
  - "_ismbchira_l (función)"
  - "_ismbckata (función)"
  - "_ismbckata_l (función)"
  - "Hiragana"
  - "ismbchira (función)"
  - "ismbchira_l (función)"
  - "ismbckata (función)"
  - "ismbdkata_l (función)"
  - "Katakana"
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbchira, _ismbchira_l, _ismbckata, _ismbckata_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Funciones concretas de la página de códigos 932**  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución.  Para obtener más información, vea [Funciones de CRT no admitidas con \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## Sintaxis  
  
```  
int _ismbchira(  
   unsigned int c   
);  
int _ismbchira_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbckata(  
   unsigned int c   
);  
int _ismbckata_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si el carácter cumple la condición de prueba o 0 si no la cumple.  Si `c` \<\= 255 y hay una rutina `_ismbb` correspondiente \(por ejemplo, `_ismbcalnum` corresponde a `_ismbbalnum`\), el resultado es el valor devuelto de la rutina `_ismbb` correspondiente.  
  
## Comentarios  
 Cada una de estas funciones prueba si un carácter multibyte dado cumple una condición determinada.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
|Rutina|Condición de prueba \(solo página de códigos 932\)|  
|------------|--------------------------------------------------------|  
|`_ismbchira`|Hiragana de doble byte: 0x829F\<\=`c`\<\=0x82F1.|  
|`_ismbchira_l`|Hiragana de doble byte: 0x829F\<\=`c`\<\=0x82F1.|  
|`_ismbckata`|Katakana de doble byte: 0x8340\=\<`c`\<\=0x8396.|  
|`_ismbckata_l`|Katakana de doble byte: 0x8340\=\<`c`\<\=0x8396.|  
  
 **Fin de funciones específicos de la página de códigos 932**  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_ismbchira`|\<mbstring.h\>|  
|`_ismbchira_l`|\<mbstring.h\>|  
|`_ismbckata`|\<mbstring.h\>|  
|`_ismbckata_l`|\<mbstring.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [\_ismbc \(Rutinas\)](../../c-runtime-library/ismbc-routines.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)