---
title: "isdigit, iswdigit, _isdigit_l, _iswdigit_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isdigit_l"
  - "iswdigit"
  - "_iswdigit_l"
  - "isdigit"
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
  - "_iswdigit_l"
  - "_isdigit_l"
  - "iswdigit"
  - "isdigit"
  - "_istdigit"
  - "_istdigit_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iswdigit (función)"
  - "iswdigit_l (función)"
  - "_iswdigit_l (función)"
  - "_istdigit_l (función)"
  - "_istdigit (función)"
  - "istdigit (función)"
  - "isdigit (función)"
  - "isdigit_l (función)"
  - "_ismbcdigit_l (función)"
  - "_isdigit_l (función)"
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# isdigit, iswdigit, _isdigit_l, _iswdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter de dígito decimal.  
  
## Sintaxis  
  
```  
int isdigit(   
   int c   
);  
int iswdigit(   
   wint_t c   
);  
int _isdigit_l(   
   int c,  
   _locale_t locale  
);  
int _iswdigit_l(   
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
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter de dígito decimal.  `isdigit` devuelve un valor distinto de cero si `c` es un dígito decimal \(0 – 9\).  `iswdigit` devuelve un valor distinto de cero si `c` es un carácter ancho que corresponde a un carácter de dígito decimal.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones con el sufijo `_l` usan la configuración regional que se pasa en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isdigit` e `_isdigit_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istdigit`|`isdigit`|[\_ismbcdigit](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswdigit`|  
|`_istdigit_l`|`_isdigit_l`|[\_ismbcdigit\_l](../../c-runtime-library/reference/ismbcalnum-functions.md)|`_iswdigit_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isdigit`|\<ctype.h\>|  
|`iswdigit`|\<ctype.h\> o \<wchar.h\>|  
|`_isdigit_l`|\<ctype.h\>|  
|`_iswdigit_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)