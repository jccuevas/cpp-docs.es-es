---
title: "tolower, _tolower, towlower, _tolower_l, _towlower_l | Microsoft Docs"
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
  - "_tolower_l"
  - "towlower"
  - "tolower"
  - "_tolower"
  - "_towlower_l"
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
  - "_totlower"
  - "tolower"
  - "_tolower"
  - "towlower"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tolower (función)"
  - "_tolower_l (función)"
  - "_totlower (función)"
  - "_towlower_l (función)"
  - "mayúsculas y minúsculas, convertir"
  - "caracteres, convertir"
  - "minúsculas, convertir a"
  - "conversión de cadenas, mayúsculas y minúsculas"
  - "conversión de cadenas, a distintos caracteres"
  - "tolower (función)"
  - "tolower_l (función)"
  - "totlower (función)"
  - "towlower (función)"
  - "towlower_l (función)"
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tolower, _tolower, towlower, _tolower_l, _towlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte un carácter en minúsculas.  
  
## Sintaxis  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### Parámetros  
 \[in\] `c`  
 Carácter que se va a convertir.  
  
 \[in\] `locale`  
 Configuración regional a utilizar para la traducción configuración regional\- concreta.  
  
## Valor devuelto  
 Cada una de estas rutinas convierte una copia de `c` a minúsculas si la conversión es posible, y devuelve el resultado.  No hay ningún valor devuelto reservado para indicar un error.  
  
## Comentarios  
 Cada una de estas rutinas convierte una letra mayúscula especificada en minúsculas si es posible y pertinente.  La conversión del caso de `towlower` es configuración regional\- concreta.  Únicamente caracteres pertinentes para la configuración regional actual se cambian en caso de que.  Las funciones sin el sufijo de `_l` utilizan la configuración regional actualmente establecido.  Las versiones de estas funciones que tienen el sufijo de `_l` toma la configuración regional como parámetro y use que en lugar de la configuración regional actualmente establecido.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Para que `_tolower` dé los resultados esperados, [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) y [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) debe ambos devuelven cero.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l` y `_towlower_l` no dependen de la configuración regional y no están diseñadas para llamarlas directamente.  Se proporcionan solo para el uso interno por parte de `_totlower_l`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`tolower`|\<ctype.h\>|  
|`_tolower`|\<ctype.h\>|  
|`towlower`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [a funciones](../../c-runtime-library/to-functions.md).  
  
## Equivalente en .NET Framework  
 [System::Char::ToLower](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [to \(Funciones\)](../../c-runtime-library/to-functions.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)