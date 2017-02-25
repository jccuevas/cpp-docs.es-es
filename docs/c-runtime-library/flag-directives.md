---
title: "Directivas de marca | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "c.flags"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "directivas de marca, función printf"
  - "campos de especificación de formato para la función printf"
  - "marca de impresión (directivas)"
  - "printf (función), especificación de formato (campos)"
ms.assetid: b00cbdc9-1e5c-4b30-9f56-c1ef8d383767
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Directivas de marca
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una especificación de formato, el primer campo opcional es `flags`.  Una directiva de marcador es un carácter que especifica la justificación del resultado y la salida de signos, de espacios en blanco, de ceros iniciales, de separadores decimales, y de prefijos octales y hexadecimales.  Más de una directiva de marcador puede aparecer en una especificación de formato, y marcadores pueden aparecer en cualquier orden.  
  
### Caracteres de marcador  
  
|Marcar|Significado|Valor|  
|------------|-----------------|-----------|  
|`–`|La izquierda alinear el resultado al ancho de campo especificado.|La derecha alinear.|  
|`+`|Utilice un signo \(\+ o –\) al prefijo el valor de salida si es de un tipo con signo.|El signo solo aparece por valores con signo negativo \(–\).|  
|`0`|Si `width` es precedido por `0`, se agregan los ceros iniciales hasta alcanzar el ancho mínimo.  Si aparecen `0` y `–` , se omite `0` .  Si `0` se especifica como formato entero \(`i`, `u`, `x`, `X`, `o`, `d`\) y una especificación de precisión está también presente\- para el ejemplo, se omite `%04.d`— `0` .|Ningún relleno.|  
|espacio en blanco \(''\)|Utilice un espacio en blanco al prefijo el valor de salida si se firma y positivo.  Se omite el espacio en blanco si tanto el aparece en blanco y \+ marcas.|Ningún espacio en blanco aparece.|  
|`#`|Cuando se utiliza con `o`, `x`, o el formato de `X` , el indicador de `#` utiliza 0, 0x, o 0X, respectivamente, el prefijo cualquier valor distinto de salida.|Ningún espacio en blanco aparece.|  
||Cuando se utiliza con `e`, `E`, `f`, `a` o formato de `A` , el indicador de `#` fuerza el valor de salida para contener un separador decimal.|El separador decimal sólo aparece si los dígitos se siguen.|  
||Cuando ha utilizado con el formato de `g` o de `G` , el indicador de `#` fuerza el valor de salida para contener un separador decimal y evita el truncamiento de ceros finales.<br /><br /> Se omite cuando se usa con `c`, `d`, `i`, `u`, o `s`.|El separador decimal sólo aparece si los dígitos se siguen.  Se truncan los ceros finales.|  
  
## Vea también  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [Sintaxis de especificación de formato: Funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)   
 [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)   
 [Especificación de tamaño](../c-runtime-library/size-specification.md)   
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)