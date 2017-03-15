---
title: "Interpretaci&#243;n de secuencias de caracteres de varios bytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.character.multibyte"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MBCS [C++], página de códigos de configuración regional"
ms.assetid: da9150de-70ea-4d2f-90e6-ddb9202dd80b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Interpretaci&#243;n de secuencias de caracteres de varios bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayoría de las rutinas de multibyte\- carácter en la biblioteca en tiempo de ejecución de Microsoft reconocen secuencias de multibyte\- carácter relativos a una página de códigos multibyte.  El valor de salida se ve afectado por el valor de la categoría `LC_CTYPE` de la configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  
  
### Rutinas Configuración regional\-dependientes de Multibyte  
  
|Rutina|Utilice|  
|------------|-------------|  
|[\_mbclen, mblen, \_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Valida y devuelve el número de bytes del carácter multibyte|  
|[strlen, wcslen, \_mbslen, \_mbslen\_l, \_mbstrlen, \_mbstrlen\_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Para las cadenas de caracteres multibyte: validar cada carácter de cadena; devuelve la longitud de la cadena.  Para las cadenas de caracteres anchos: longitud de vuelta de la cadena.|  
|[mbstowcs, \_mbstowcs\_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md), [mbstowcs\_s, \_mbstowcs\_s\_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Convierte la secuencia de caracteres multibyte en la secuencia correspondiente de caracteres anchos|  
|[mbtowc, \_mbtowc\_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Convierte el carácter multibyte en el carácter ancho correspondiente|  
|[wcstombs, \_wcstombs\_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs\_s, \_wcstombs\_s\_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Convierte la secuencia de caracteres anchos en la secuencia correspondiente de caracteres multibyte|  
|[wctomb, \_wctomb\_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb\_s, \_wctomb\_s\_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Convierte el carácter ancho en el carácter multibyte correspondiente|  
  
## Vea también  
 [Internacionalización](../c-runtime-library/internationalization.md)   
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)