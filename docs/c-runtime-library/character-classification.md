---
title: "Clasificaci&#243;n de caracteres | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types.character"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "rutinas de clasificación de caracteres"
  - "caracteres, pruebas"
ms.assetid: 3b6c8f0b-9701-407a-b384-9086698773f5
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Clasificaci&#243;n de caracteres
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cada una de estas rutinas prueba un carácter de un solo byte, un carácter ancho o un carácter multibyte especificado para ver si cumple una condición. Por definición, los caracteres ASCII entre 0 y 127 son un subconjunto de todos los juegos de caracteres multibyte.  Por ejemplo, el katakana japonés contiene caracteres ASCII y no ASCII.  
  
 El valor de la categoría `LC_CTYPE` de la configuración regional afecta a las condiciones de prueba; vea [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) para obtener más información.  Las versiones de estas funciones sin el sufijo `_l` usan la configuración regional actual de su comportamiento dependiente de la configuración regional; las versiones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en su lugar.  
  
 Estas rutinas se suelen ejecutar más rápidamente que las pruebas que se escriban y deben usarse preferentemente.  Por ejemplo, el código siguiente es más lento en ejecutarse que una llamada a `isalpha(c)`:  
  
```  
if ((c >= 'A') && (c <= 'Z')) || ((c >= 'a') && (c <= 'z'))  
    return TRUE;  
```  
  
### Rutinas de clasificación de caracteres  
  
|Rutina|Condición de prueba de caracteres|Equivalente de .NET Framework|  
|------------|---------------------------------------|-----------------------------------|  
|[isalnum, iswalnum, \_isalnum\_l, \_iswalnum\_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md), [\_ismbcalnum, \_ismbcalnum\_l, \_ismbcalpha, \_ismbcalpha\_l, \_ismbcdigit, \_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumérico|[System::Char::IsLetterOrDigit](https://msdn.microsoft.com/en-us/library/system.char.isletterordigit.aspx).|  
|[\_ismbcalnum, \_ismbcalnum\_l, \_ismbcalpha, \_ismbcalpha\_l, \_ismbcdigit, \_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfanumérico|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[isalpha, iswalpha, \_isalpha\_l, \_iswalpha\_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md), [\_ismbcalnum, \_ismbcalnum\_l, \_ismbcalpha, \_ismbcalpha\_l, \_ismbcdigit, \_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Alfabético|[\<caps:sentence id\="tgt20" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isascii, \_\_isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|ASCII|[\<caps:sentence id\="tgt22" sentenceid\="7985fd1b5b2aeb907c06a172679a27b2" class\="tgtSentence"\>System::Char::IsLetter\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)|  
|[isblank, iswblank, \_isblank\_l, \_iswblank\_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md), [\_ismbcsblank, \_ismbcsblank\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Espacio en blanco \(espacio o tabulación horizontal\)|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).|  
|[iscntrl, iswcntrl, \_iscntrl\_l, \_iswcntrl\_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|Control|[\<caps:sentence id\="tgt29" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym, iscsymf, \_\_iscsym, \_\_iswcsym, \_\_iscsymf, \_\_iswcsymf, \_iscsym\_l, \_iswcsym\_l, \_iscsymf\_l, \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|Letra, carácter de subrayado o dígito|[\<caps:sentence id\="tgt31" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[iscsym, iscsymf, \_\_iscsym, \_\_iswcsym, \_\_iscsymf, \_\_iswcsymf, \_iscsym\_l, \_iswcsym\_l, \_iscsymf\_l, \_iswcsymf\_l](../c-runtime-library/reference/iscsym-functions.md)|Letra o carácter de subrayado|[\<caps:sentence id\="tgt33" sentenceid\="9528bc8d4eee1fcafa3dca9e9901915d" class\="tgtSentence"\>System::Char::IsControl\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iscontrol.aspx)|  
|[isdigit, iswdigit, \_isdigit\_l, \_iswdigit\_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md), [\_ismbcalnum, \_ismbcalnum\_l, \_ismbcalpha, \_ismbcalpha\_l, \_ismbcdigit, \_ismbcdigit\_l](../c-runtime-library/reference/ismbcalnum-functions.md)|Dígito decimal|[\<caps:sentence id\="tgt36" sentenceid\="20b77d76c6cf167a186925e085420e65" class\="tgtSentence"\>System::Char::IsDigit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)|  
|[isgraph, iswgraph, \_isgraph\_l, \_iswgraph\_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md), [\_ismbcgraph, \_ismbcgraph\_l, \_ismbcprint, \_ismbcprint\_l, \_ismbcpunct, \_ismbcpunct\_l, \_ismbcblank, \_ismbcblank\_l, \_ismbcspace, \_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Carácter imprimible distinto de espacio|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[islower, iswlower, \_islower\_l, \_iswlower\_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md), [\_ismbclower, \_ismbclower\_l, \_ismbcupper, \_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Minúsculas|[\<caps:sentence id\="tgt44" sentenceid\="5e79724bd080c040f5d77abaa610244d" class\="tgtSentence"\>System::Char::IsLower\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)|  
|[\_ismbchira, \_ismbchira\_l, \_ismbckata, \_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Hiragana|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbchira, \_ismbchira\_l, \_ismbckata, \_ismbckata\_l](../c-runtime-library/reference/ismbchira-ismbchira-l-ismbckata-ismbckata-l.md)|Katakana|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbclegal, \_ismbclegal\_l, \_ismbcsymbol, \_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Carácter multibyte válido|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbcl0, \_ismbcl0\_l, \_ismbcl1, \_ismbcl1\_l, \_ismbcl2, \_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Carácter multibyte nivel 0 de Japón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbcl0, \_ismbcl0\_l, \_ismbcl1, \_ismbcl1\_l, \_ismbcl2, \_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Carácter multibyte nivel 1 de Japón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbcl0, \_ismbcl0\_l, \_ismbcl1, \_ismbcl1\_l, \_ismbcl2, \_ismbcl2\_l](../c-runtime-library/reference/ismbcl0-ismbcl0-l-ismbcl1-ismbcl1-l-ismbcl2-ismbcl2-l.md)|Carácter multibyte nivel 2 de Japón|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[\_ismbclegal, \_ismbclegal\_l, \_ismbcsymbol, \_ismbcsymbol\_l](../c-runtime-library/reference/ismbclegal-ismbclegal-l-ismbcsymbol-ismbcsymbol-l.md)|Carácter multibyte no alfanumérico|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[isprint, iswprint, \_isprint\_l, \_iswprint\_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md), [\_ismbcgraph, \_ismbcgraph\_l, \_ismbcprint, \_ismbcprint\_l, \_ismbcpunct, \_ismbcpunct\_l, \_ismbcblank, \_ismbcblank\_l, \_ismbcspace, \_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Carácter imprimible|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[ispunct, iswpunct, \_ispunct\_l, \_iswpunct\_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md), [\_ismbcgraph, \_ismbcgraph\_l, \_ismbcprint, \_ismbcprint\_l, \_ismbcpunct, \_ismbcpunct\_l, \_ismbcblank, \_ismbcblank\_l, \_ismbcspace, \_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Puntuación|[\<caps:sentence id\="tgt80" sentenceid\="d38bbde5482b110a63876458567db603" class\="tgtSentence"\>System::Char::IsPunctuation\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.ispunctuation.aspx)|  
|[isspace, iswspace, \_isspace\_l, \_iswspace\_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md), [\_ismbcgraph, \_ismbcgraph\_l, \_ismbcprint, \_ismbcprint\_l, \_ismbcpunct, \_ismbcpunct\_l, \_ismbcblank, \_ismbcblank\_l, \_ismbcspace, \_ismbcspace\_l](../c-runtime-library/reference/ismbcgraph-functions.md)|Espacio en blanco|[\<caps:sentence id\="tgt83" sentenceid\="acbb8b5269b25caa0be79d70895dc079" class\="tgtSentence"\>System::Char::IsWhiteSpace\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)|  
|[Isupper, iswupper](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md), [\_ismbclower, \_ismbclower\_l, \_ismbcupper, \_ismbcupper\_l](../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|Mayúsculas|[\<caps:sentence id\="tgt86" sentenceid\="7f17c3dfa91d5cdf120546eae2131f1f" class\="tgtSentence"\>System::Char::IsUpper\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)|  
|[\_isctype, iswctype, \_isctype\_l, \_iswctype\_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|Propiedad especificada por el argumento de `desc`|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
|[isxdigit, iswxdigit, \_isxdigit\_l, \_iswxdigit\_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|Dígito hexadecimal|[\<caps:sentence id\="tgt92" sentenceid\="ce7b0e5c510cf706d10a80a8594068ce" class\="tgtSentence"\>System::Char::IsNumber\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.char.isnumber.aspx)|  
|[\_mbclen, mblen, \_mblen\_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Longitud devuelta del caracteres multibyte válidos. El resultado depende del valor de la categoría de `LC_CTYPE` de la configuración regional actual|No es aplicable  Para llamar a la función estándar de C, use `PInvoke`.  Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).|  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)