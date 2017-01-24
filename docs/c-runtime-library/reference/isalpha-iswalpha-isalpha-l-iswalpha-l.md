---
title: "isalpha, iswalpha, _isalpha_l, _iswalpha_l | Microsoft Docs"
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
  - "iswalpha"
  - "_iswalpha_l"
  - "isalpha"
  - "_isalpha_l"
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
  - "_istalpha"
  - "_ismbcalpha_l"
  - "isalpha"
  - "_isalpha_l"
  - "iswalpha"
  - "_istalpha_l"
  - "_iswalpha_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isalpha_l (función)"
  - "_ismbcalpha (función)"
  - "_ismbcalpha_l (función)"
  - "_istalpha (función)"
  - "_istalpha_l (función)"
  - "_iswalpha_l (función)"
  - "isalpha (función)"
  - "istalpha (función)"
  - "iswalpha (función)"
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isalpha, iswalpha, _isalpha_l, _iswalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter alfabético.  
  
## Sintaxis  
  
```  
int isalpha(   
   int c   
);  
int iswalpha(   
   wint_t c   
);  
int _isalpha_l(   
   int c,  
   _locale_t locale   
);  
int _iswalpha_l(   
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar en lugar de la configuración regional actual.  
  
## Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter alfabético.  `isalpha` devuelve un valor distinto de cero si `c` está en los intervalos A – Z o a – z.  `iswalpha` devuelve un valor distinto de cero solo para caracteres anchos para los que `iswupper` o `iswlower` es distinto de cero; es decir, para cualquier carácter ancho que pertenezca a un juego definido por la implementación para el que ni `iswcntrl`, ni `iswdigit` ni `iswpunct` ni `iswspace` sea distinto de cero.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isalpha` e `_isalpha_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istalpha`|`isalpha`|`_ismbcalpha`|`iswalpha`|  
|`_istalpha_l`|`_isalpha_l`|`_ismbcalpha_l`|`_iswalpha_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`isalpha`|\<ctype.h\>|  
|`iswalpha`|\<ctype.h\> o \<wchar.h\>|  
|`_isalpha_l`|\<ctype.h\>|  
|`_iswalpha_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)