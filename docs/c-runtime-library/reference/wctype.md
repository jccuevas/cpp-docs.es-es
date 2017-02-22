---
title: "wctype | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wctype"
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
apitype: "DLLExport"
f1_keywords: 
  - "wctype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wctype (función)"
  - "caracteres anchos"
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# wctype
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Determina una regla de clasificación de los códigos de carácter ancho.  
  
## Sintaxis  
  
```  
wctype_t wctype(  
   const char * property   
);  
```  
  
#### Parámetros  
 `property`  
 Cadena de la propiedad.  
  
## Valor devuelto  
 Si la categoría de `LC_CTYPE` de la configuración regional actual no define una regla de clasificación cuyo nombre coincida con la cadena `property`de propiedades, la función devuelve cero.  De lo contrario, devuelve un valor distinto de cero adecuado para el uso como segundo argumento a una llamada subsiguiente a [towctrans](../../c-runtime-library/reference/towctrans.md).  
  
## Comentarios  
 La función determina una regla de clasificación de los códigos de carácter ancho.  Los siguientes pares de llamadas tienen el mismo comportamiento en todas las configuraciones regionales \(solo una implementación puede definir reglas adicionales de clasificación incluso en la configuración regional “c”\):  
  
|Función|Igual que|  
|-------------|---------------|  
|`iswalnum(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alnum" ) )`|  
|`iswalpha(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alpha" ) )`|  
|`iswcntrl(`  `c`  `)`|`iswctype(`  `c` `, wctype( "cntrl" ) )`|  
|`iswdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "digit" ) )`|  
|`iswgraph(`  `c`  `)`|`iswctype(`  `c` `, wctype( "graph" ) )`|  
|`iswlower(`  `c`  `)`|`iswctype(`  `c` `, wctype( "lower" ) )`|  
|`iswprint(`  `c`  `)`|`iswctype(`  `c` `, wctype( "print" ) )`|  
|`iswpunct(`  `c`  `)`|`iswctype(`  `c` `, wctype( "punct" ) )`|  
|`iswspace(`  `c`  `)`|`iswctype(`  `c` `, wctype( "space" ) )`|  
|`iswupper(`  `c`  `)`|`iswctype(`  `c` `, wctype( "upper" ) )`|  
|`iswxdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "xdigit" ) )`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`wctype`|\<wctype.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)