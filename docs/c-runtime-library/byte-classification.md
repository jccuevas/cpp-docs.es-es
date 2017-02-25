---
title: "Clasificaci&#243;n de bytes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types.bytes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rutinas de clasificación de bytes"
  - "bytes, pruebas"
  - "página de códigos 932"
ms.assetid: 1cb52d71-fb0c-46ca-aad7-6472c1103370
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Clasificaci&#243;n de bytes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de estas rutinas prueba un byte especificado de un carácter multibyte por satisfacción de una condición.  Excepto donde especificado de otra forma, el valor de salida es afectado por el valor de la categoría de `LC_CTYPE` de configuración regional; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  
  
> [!NOTE]
>  Por definición, los caracteres ASCII entre 0 y 127 son un subconjunto de todos los juegos de caracteres multibyte.  Por ejemplo, el juego de caracteres japonés de las katakanas incluye caracteres ASCII así como no ASCII.  
  
 Las constantes predefinidas en la tabla siguiente se definen en CTYPE.H.  
  
### Rutinas de la Byte\- evaluación de Multibyte\- carácter  
  
|Rutina|Condición de prueba de byte|Equivalente de .NET Framework|  
|------------|---------------------------------|-----------------------------------|  
|[isleadbyte, \_isleadbyte\_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Byte inicial; el resultado de pruebas depende del valor de la categoría de `LC_CTYPE` de la configuración regional actual|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbalnum, \_ismbbalnum\_l](../c-runtime-library/reference/ismbbalnum-ismbbalnum-l.md)|`isalnum &#124;&#124; _ismbbkalnum`|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbalpha, \_ismbbalpha\_l](../c-runtime-library/reference/ismbbalpha-ismbbalpha-l.md)|`isalpha &#124;&#124; _ismbbkalnum`|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbgraph, \_ismbbgraph\_l](../c-runtime-library/reference/ismbbgraph-ismbbgraph-l.md)|Igual que `_ismbbprint`, pero `_ismbbgraph` no incluye el carácter de espacio \(0x20\)|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkalnum, \_ismbbkalnum\_l](../c-runtime-library/reference/ismbbkalnum-ismbbkalnum-l.md)|Símbolo de texto no ASCII que no sea de puntuación.  Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkalnum` prueba para las katakanas alfanuméricas|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkana, \_ismbbkana\_l](../c-runtime-library/reference/ismbbkana-ismbbkana-l.md)|Katakana \(0xA1 – 0xDF\), página de códigos 932 únicamente|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkprint, \_ismbbkprint\_l](../c-runtime-library/reference/ismbbkprint-ismbbkprint-l.md)|Texto no ASCII o signo de puntuación no ASCII.  Por ejemplo, solo en la página de códigos 932, `_ismbbkprint` comprueba si hay caracteres o signos de puntuación katakana \(intervalo: 0xA1 – 0xDF\).|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbkpunct, \_ismbbkpunct\_l](../c-runtime-library/reference/ismbbkpunct-ismbbkpunct-l.md)|Puntuación no ASCII.  Por ejemplo, en la página de códigos 932 únicamente, `_ismbbkpunct` prueba si hay signos de puntuación katakana.|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbblead, \_ismbblead\_l](../c-runtime-library/reference/ismbblead-ismbblead-l.md)|Primer byte de un carácter multibyte.  Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x81 – 0x9F y 0xE0 – 0xFC.|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbprint, \_ismbbprint\_l](../c-runtime-library/reference/ismbbprint-ismbbprint-l.md)|`isprint &#124;&#124; _ismbbkprint. ismbbprint` incluye el carácter de espacio \(0x20\)|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbpunct, \_ismbbpunct\_l](../c-runtime-library/reference/ismbbpunct-ismbbpunct-l.md)|`ispunct &#124;&#124; _ismbbkpunct`|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbbtrail, \_ismbbtrail\_l](../c-runtime-library/reference/ismbbtrail-ismbbtrail-l.md)|Segundo byte de un carácter multibyte.  Por ejemplo, en la página de códigos 932 únicamente, los intervalos válidos son 0x40 – 0x7E y 0x80 – 0xEC.|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_ismbslead, \_ismbslead\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Byte inicial \(en contexto de string\)|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[ismbstrail, \_ismbstrail\_l](../c-runtime-library/reference/ismbslead-ismbstrail-ismbslead-l-ismbstrail-l.md)|Byte final \(en contexto de string\)|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_mbbtype, \_mbbtype\_l](../c-runtime-library/reference/mbbtype-mbbtype-l.md)|Tipo devuelto del byte por byte anterior|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[\_mbsbtype, \_mbsbtype\_l](../c-runtime-library/reference/mbsbtype-mbsbtype-l.md)|Tipo de valor devuelto de bytes en la cadena|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
|[mbsinit](../c-runtime-library/reference/mbsinit.md)|Realiza el seguimiento del estado de una conversión de caracteres multibyte.|No aplicable, pero vea [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)|  
  
 La macro de `MB_LEN_MAX` , definida en LIMITS.H, expanda a la longitud máxima en bytes que cualquier carácter multibyte puede tener.  `MB_CUR_MAX`, definido en STDLIB.H, expanda a la longitud máxima en bytes de cualquier carácter multibyte en la configuración regional actual.  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)