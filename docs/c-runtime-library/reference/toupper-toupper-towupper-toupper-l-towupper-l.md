---
title: "toupper, _toupper, towupper, _toupper_l, _towupper_l | Microsoft Docs"
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
  - "_toupper_l"
  - "towupper"
  - "toupper"
  - "_towupper_l"
  - "_toupper"
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
  - "towupper"
  - "_toupper"
  - "_totupper"
  - "toupper"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_totupper (función)"
  - "_toupper (función)"
  - "_toupper_l (función)"
  - "_towupper_l (función)"
  - "mayúsculas y minúsculas, convertir"
  - "caracteres, convertir"
  - "conversión de cadenas, mayúsculas y minúsculas"
  - "conversión de cadenas, a distintos caracteres"
  - "totupper (función)"
  - "toupper (función)"
  - "toupper_l (función)"
  - "towupper (función)"
  - "towupper_l (función)"
  - "mayúsculas, convertir cadenas en"
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# toupper, _toupper, towupper, _toupper_l, _towupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierta el carácter a mayúsculas.  
  
## Sintaxis  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada una de estas rutinas convierte una copia de `c`, si es posible, y devuelve el resultado.  
  
 Si `c` es un carácter ancho por el que `iswlower` es distinto de cero y hay un carácter ancho correspondiente que `iswupper` es distinto de cero, `towupper` devuelve el carácter ancho correspondiente; si no, `towupper` devuelve `c` sin modificar.  
  
 No hay ningún valor devuelto reservado para indicar un error.  
  
 Para que `toupper` dé los resultados esperados, [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) y [islower](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) debe ambos devuelven cero.  
  
## Comentarios  
 Cada una de estas rutinas convierte una minúscula especificada a una letra mayúscula si es posible y adecuado.  La conversión del caso de `towupper` es configuración regional\- concreta.  Únicamente caracteres pertinentes para la configuración regional actual se cambian en caso de que.  Las funciones sin el sufijo de `_l` utilizan la configuración regional actualmente establecido.  Las versiones de estas funciones con el sufijo de `_l` toman la configuración regional como parámetro y utilizan que en lugar de la configuración regional actualmente establecido.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Para que `toupper` dé los resultados esperados, [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) y [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) debe ambos devuelven cero.  
  
 [Rutinas de conversión de datos](../../c-runtime-library/data-conversion.md)  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l` y `_towupper_l` no dependen de la configuración regional y no están diseñadas para llamarlas directamente.  Se proporcionan solo para el uso interno por parte de `_totupper_l`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`toupper`|\<ctype.h\>|  
|`_toupper`|\<ctype.h\>|  
|`towupper`|\<ctype.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea el ejemplo de [a funciones](../../c-runtime-library/to-functions.md).  
  
## Equivalente en .NET Framework  
 [System::Char::ToUpper](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)  
  
## Vea también  
 [is, isw \(Rutinas\)](../../c-runtime-library/is-isw-routines.md)   
 [to \(Funciones\)](../../c-runtime-library/to-functions.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)