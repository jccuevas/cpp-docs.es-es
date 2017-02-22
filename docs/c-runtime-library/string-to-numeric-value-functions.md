---
title: "Funciones de conversi&#243;n de valores de cadena en valores num&#233;ricos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstoui64"
  - "_tcstoi64"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "analizar, cadenas numéricas"
  - "conversión de cadenas, a valores numéricos"
ms.assetid: 11cbd9ce-033b-4914-bf66-029070e7e385
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Funciones de conversi&#243;n de valores de cadena en valores num&#233;ricos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

-   [strtod, \_strtod\_l, wcstod, \_wcstod\_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)  
  
-   [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)  
  
-   [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)  
  
-   [\_strtoi64, \_wcstoi64, \_strtoi64\_l, \_wcstoi64\_l](../c-runtime-library/reference/strtoi64-wcstoi64-strtoi64-l-wcstoi64-l.md)  
  
-   [\_strtoui64, \_wcstoui64, \_strtoui64\_l, \_wcstoui64\_l](../c-runtime-library/reference/strtoui64-wcstoui64-strtoui64-l-wcstoui64-l.md)  
  
## Comentarios  
 Cada función de la familia de **strtod** convierte una cadena terminada en null a un valor numérico.  Las funciones disponibles se muestran en la tabla siguiente.  
  
|Función|Descripción|  
|-------------|-----------------|  
|`strtod`|Cadena de convierte el valor de doble precisión de punto flotante|  
|`strtol`|Cadena convert el entero largo|  
|`strtoul`|Cadena convert el entero unsigned long|  
|`_strtoi64`|Cadena de convertir en un entero de 64 bits de `__int64`|  
|`_strtoui64`|Cadena de convertir en un entero de 64 bits sin signo de `__int64`|  
  
 `wcstod`, `wcstol`, `wcstoul`, y `_wcstoi64` son versiones de caracteres anchos de `strtod`, de `strtol`, de `strtoul`, y de `_strtoi64`, respectivamente.  El argumento de cadena a cada una de estas funciones de carácter ancho es una cadena de caracteres; cada función se comporta idénticamente a su equivalente de solo\-byte\- carácter de otra manera.  
  
 La función de `strtod` toma dos argumentos: el primero es la cadena de entrada, y la segunda un puntero al carácter que finaliza el proceso de conversión.  `strtol`, `strtoul`, **\_strtoi64** y **\_strtoui64** tienen un tercer argumento como base de número el uso en el proceso de conversión.  
  
 La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  Cada función finaliza la lectura de la cadena del primer carácter que no puede reconocer como parte de un número.  Este puede ser el carácter null final.  Para `strtol`, `strtoul`, `_strtoi64`, y `_strtoui64`, este carácter de terminación también puede ser el primer carácter numérico es mayor o igual que la base de número usuario\- proporcionada.  
  
 Si el puntero usuario\- proporcionado un carácter de la FIN\-de\- conversión no se establece en **nulo** en tiempo de llamada, un puntero al carácter que se detuvo el análisis se almacenará allí en su lugar.  Si ninguna conversión se puede realizar \(no se encontraron dígitos válidos o base no válida se especificó\), el valor del puntero de la cadena se almacena en esa dirección.  
  
 `strtod` cuenta con una cadena con el formato siguiente:  
  
 \[*espacio en blanco*\] \[*sign*\] \[`digits`\] \[**.**`digits`\] \[{**x** &#124; **D** &#124; **e** &#124; **E**} \[*sign*\]`digits`\]  
  
 *Un espacio en blanco* puede ser el espacio o caracteres de tabulación, se omiten que; *el signo* es más \(**\+**\) o menos \(**–**\); y `digits` es uno o más dígitos decimales.  Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base.  Los dígitos decimales pueden ir seguidos por un exponente, formada por una letra preliminar \(**x**, **L**, **h**, o **E**\) y un entero opcionalmente firmado.  Si no aparece una parte del exponente ni un carácter de base, se supondrá que el carácter de base sigue el último dígito de la cadena.  El primer carácter que no se ajusta a este formato detiene el análisis.  
  
 `strtol`, `strtoul`, `_strtoi64`, y las funciones de `_strtoui64` esperan una cadena con el formato siguiente:  
  
 \[*espacio en blanco*\] \[{**\+** &#124; **–**}\] \[**0** \[{ **x** &#124; **X** }\]\] \[`digits`\]  
  
 Si el argumento base está entre 2 y 36, se utiliza como base del número.  Si es 0, los caracteres iniciales que hace referencia el puntero de la FIN\-de\- conversión se utilizan para determinar la base.  Si el primer carácter es 0 y el segundo carácter no es “x” o “X”, la cadena se interpreta como entero octal; si no, se interpreta como un número decimal.  Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal.  Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal.  Las letras” a la “z” \(o “A” a la “z "\) se asignan los valores 10 a 35; sólo las letras cuyo asignaban valores son menos que *la base* se permiten.  `strtoul` y `_strtoui64` permiten especificar más \(**\+**\) o menos prefijo de signo \(de**–**\); un signo menos principal indica que el valor devuelto se negado.  
  
 El valor de salida se ve afectado por el valor de la categoría `LC_NUMERIC` de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo **\_l** usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo **\_l** son idénticas salvo que usan el parámetro de configuración regional que se pasa.  
  
 Cuando funciona el valor devuelto por estos provocaría un desbordamiento o un subdesbordamiento, o cuando la conversión no son valores de posible caso, especial cambian como se muestra a continuación:  
  
|Función|Condition|Valor devuelto|  
|-------------|---------------|--------------------|  
|`strtod`|Desbordamiento|\+\/\- `HUGE_VAL`|  
|`strtod`|Subdesbordamiento o ninguna conversión|0|  
|`strtol`|\+ Desbordamiento|**LONG\_MAX**|  
|`strtol`|\- Desbordamiento|**LONG\_MIN**|  
|`strtol`|Subdesbordamiento o ninguna conversión|0|  
|`_strtoi64`|\+ Desbordamiento|**\_I64\_MAX**|  
|`_strtoi64`|\- Desbordamiento|**\_I64\_MIN**|  
|`_strtoi64`|Ninguna conversión|0|  
|`_strtoui64`|Desbordamiento|**\_UI64\_MAX**|  
|`_strtoui64`|Ninguna conversión|0|  
  
 **\_I64\_MAX**, \_**I64\_MIN**, y **\_UI64\_MAX** se definen en LIMITS.H.  
  
 `wcstod`, `wcstol`, `wcstoul`, `_wcstoi64`, y `_wcstoui64` son versiones de caracteres anchos de `strtod`, de `strtol`, de `strtoul`, de `_strtoi64`, y de `_strtoui64`, respectivamente; el puntero a un argumento de la FIN\-de\- conversión a cada una de estas funciones de carácter ancho es una cadena de caracteres.  Si no, cada una de estas funciones de carácter ancho se comporta idénticamente a su equivalente de solo\-byte\- carácter.  
  
## Vea también  
 [Conversión de datos](../c-runtime-library/data-conversion.md)   
 [Configuración regional](../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Compatibilidad con el punto flotante](../c-runtime-library/floating-point-support.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)