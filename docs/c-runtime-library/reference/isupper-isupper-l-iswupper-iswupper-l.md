---
title: "isupper, _isupper_l, iswupper, _iswupper_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "isupper"
  - "iswupper"
  - "_iswupper_l"
  - "_isupper_l"
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
  - "isupper"
  - "_istupper"
  - "iswupper"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_istupper (función)"
  - "_isupper_l (función)"
  - "_iswupper_l (función)"
  - "istupper (función)"
  - "isupper (función)"
  - "isupper_l (función)"
  - "iswupper (función)"
  - "iswupper_l (función)"
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# isupper, _isupper_l, iswupper, _iswupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter en mayúscula.  
  
## Sintaxis  
  
```  
int isupper(  
   int c   
);  
int _isupper_l (  
   int c,  
   _locale_t locale  
);  
int iswupper(  
   wint_t c   
);  
int _iwsupper_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de una letra mayúscula.  `isupper` devuelve un valor distinto de cero si `c` es un carácter en mayúscula \(A – Z\).  `iswupper` devuelve un valor distinto de cero si `c` es un carácter ancho que corresponde a una letra mayúscula, o si `c` pertenece a un juego de caracteres anchos definido por la implementación para el que ni `iswcntrl`, ni `iswdigit`, ni `iswpunct`, ni `iswspace` es distinto de cero.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones con el sufijo `_l` usan la configuración regional que se pasa en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isupper` e `_isupper_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istupper`|`isupper`|[\_ismbcupper](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswupper`|  
|`_istupper_l`|`_isupper_l`|[\_ismbclower, \_ismbclower\_l, \_ismbcupper, \_ismbcupper\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_iswupper_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isupper`|\<ctype.h\>|  
|`_isupper_l`|\<ctype.h\>|  
|`iswupper`|\<ctype.h\> o \<wchar.h\>|  
|`_iswupper_l`|\<ctype.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsUpper](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)