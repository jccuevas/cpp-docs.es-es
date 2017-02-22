---
title: "islower, iswlower, _islower_l, _iswlower_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswlower"
  - "_islower_l"
  - "islower"
  - "_iswlower_l"
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
  - "_istlower"
  - "islower"
  - "_ismbclower_l"
  - "_liswlower_l"
  - "_istlower_l"
  - "_iswlower_l"
  - "_islower _l"
  - "_islower_l"
  - "iswlower"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_islower _l (función)"
  - "_islower_l (función)"
  - "_ismbclower_l (función)"
  - "_istlower (función)"
  - "_istlower_l (función)"
  - "_iswlower_l (función)"
  - "_liswlower_l (función)"
  - "islower (función)"
  - "istlower (función)"
  - "iswlower (función)"
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# islower, iswlower, _islower_l, _iswlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina si un entero representa un carácter en minúscula.  
  
## Sintaxis  
  
```  
int islower(  
   int c   
);  
int iswlower(  
   wint_t c   
);  
int islower_l(  
   int c,  
   _locale_t locale  
);  
int _iswlower_l(  
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
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter en minúscula.  `islower` devuelve un valor distinto de cero si `c` es un carácter en minúscula \(a – z\).  `iswlower` devuelve un valor distinto de cero si `c` es un carácter ancho que corresponde a una letra minúscula, o si `c` pertenece a un juego de caracteres anchos definido por la implementación para el que ni `iswcntrl`, ni `iswdigit`, ni `iswpunct`, ni `iswspace` es distinto de cero.  Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones con el sufijo `_l` usan la configuración regional que se pasa en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `islower` e `_islower_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos.  Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_istlower`|`islower`|[\_ismbclower](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswlower`|  
|`_istlower_l`|`_islower _l`|[\_ismbclower\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_liswlower_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`islower`|\<ctype.h\>|  
|`iswlower`|\<ctype.h\> o \<wchar.h\>|  
|`_islower_l`|\<ctype.h\>|  
|`_swlower_l`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Equivalente en .NET Framework  
 [System::Char::IsLower](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)  
  
## Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)